# PastPhoto

PastPhoto ist eine komplett native, offline-fähige iOS / iPadOS App (erstellt in Swift Playgrounds), die beliebige Videos mit wenigen Klicks in echte, animierte Apple Live Photos konvertiert. 

## Features
* **100% On-Device:** Keine Server, keine Cloud, keine Ladezeiten. Alle Videos werden lokal und sicher auf dem Gerät verarbeitet.
* **Natives Liquid Glass Design:** Nutzt die modernsten iOS-Designkomponenten (`.glassEffect()`) für ein immersives und natives Erlebnis.
* **Automatische Live Photo Erkennung:** Injiziert spezielle Metadaten (`com.apple.quicktime.content.identifier` & `MakerApple 17`), sodass die native Fotos-App das Ergebnis sofort als echtes Live Photo abspielt.
* **Hardwarebeschleunigung:** Verwendet `AVFoundation` und `CoreGraphics` für blitzschnelles Trimmen und Transkodieren.
* **Experimenteller Modus:** Standardmäßig werden Videos optimal auf 2,5 Sekunden getrimmt. Der experimentelle Modus erlaubt die Konvertierung längerer Videos.

## Voraussetzungen
* iOS / iPadOS 18+ (kompatibel mit iOS 26 Liquid Glass)
* Swift Playgrounds (oder Xcode)
* Berechtigung: "Photo Library (Add Only)"

## Installation (Swift Playgrounds)
1. Öffne die App `Swift Playgrounds` auf deinem iPad.
2. Erstelle ein neues App-Projekt.
3. Kopiere die Dateien aus dem Ordner `swift-app` in dein Projekt.
4. Stelle sicher, dass in den App-Einstellungen (App Settings -> Capabilities) die Berechtigung für die **Photo Library** aktiviert ist.

## Architektur
Das Projekt besteht aus vier Kernkomponenten:
* `ContentView.swift`: Das UI (Liquid Glass Design) und der Video-Picker.
* `PastPhotoViewModel.swift`: Der Main-Actor, der die Logik steuert und das UI updatet.
* `MediaProcessor.swift`: Verarbeitet das Video. Trimmt es, exportiert es als H.264 `MOV` und extrahiert den Key-Frame als `HEIC`. Es brennt den generierten UUID-Identifier tief in die Metadaten beider Dateien.
* `LivePhotoSaver.swift`: Nimmt die beiden verarbeiteten Dateien und vereint sie mittels `PHAssetCreationRequest` zu einem Live Photo in der Mediathek.

## Autor
Erstellt als On-Device Lösung ohne Backend-Abhängigkeiten.
