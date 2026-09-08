# Nicos MediaChecker

Native macOS-App zur technischen Prüfung von Mediendateien. Sie liest Video, Audio und Bilder mit der mitgelieferten MediaInfo-Bibliothek aus und zeigt die Angaben, die in Schnitt und Postproduktion zählen – ohne die Datei zu verändern.

## Datei analysieren

Eine Datei per Drag-and-Drop auf das Fenster legen oder über **Öffnen** (`Cmd+O`) auswählen. Unterstützt werden Formate, die MediaInfo erkennt: Video, Audio und Bilder.

Die Analyse läuft lokal. Nach dem Laden stehen Zusammenfassung, einzelne Streams und der vollständige Rohreport bereit.

## Zusammenfassung

Die Startansicht verdichtet den Report auf die relevanten Kennwerte:

- Auflösung (z. B. HD 1080, UHD 4K, DCI 4K)
- Bildrate inklusive CFR/VFR und Progressive/Interlaced
- Video-Codec, Farbraum, Abtastung (z. B. 10 bit 4:2:2) und HDR
- Datenrate, Audio-Layout und Start-Timecode

Chips springen per Klick zum zugehörigen Stream.

## Technische Hinweise

Die App prüft typische Fallstricke und zeigt sie als Hinweise (Info, Warnung, kritisch), unter anderem:

- unvollständige / abgeschnittene Datei
- variable Bildrate, Interlaced-Material, NTSC-Raten
- Rotations-Flag, fehlende Farbmetadaten, HDR ohne Transferkurve
- 8-bit-Material, Samplerate abweichend von 48 kHz, Audio-Versatz
- Drop-Frame-Timecode und nicht durchgehenden Timecode

## Streams und Felder

In der Seitenleiste stehen alle erkannten Streams: Allgemein, Video, Audio, Untertitel, Bild, Timecode und Kapitel.

Pro Stream sind die Felder thematisch gruppiert (Bild, Codec, Farbe, Kanäle, Sampling, …) und auf Deutsch beschriftet. Über **Alle Felder** werden zusätzlich die restlichen MediaInfo-Felder eingeblendet.

Die Suche in der Toolbar filtert Felder und Werte über alle Streams.

## Kopieren und Rohdaten

Über das Menü **Teilen** oder die Tastaturkürzel:

| Aktion | Kürzel |
|---|---|
| Datei öffnen | `Cmd+O` |
| Erneut analysieren | `Cmd+R` |
| Im Finder zeigen | `Cmd+Shift+R` |
| Tech-Zusammenfassung kopieren | `Cmd+Shift+C` |

Zusätzlich kopierbar: der vollständige MediaInfo-Text und das XML. Beide Rohformate sind auch als eigene Seitenleisten-Einträge sichtbar.

Die Tech-Zusammenfassung ist ein Einzeiler zum Weitergeben in Tickets oder Chats, inklusive der erkannten Hinweise.

## Technik

- macOS 26, SwiftUI
- gebündelte MediaInfo `libmediainfo` 26.05 (arm64)
- Bundle-ID: `de.filmwork.NicosMediaChecker`
