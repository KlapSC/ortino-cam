# Mitmachen bei ortino.CAM

Schön, dass du mithelfen möchtest. **Der Quelltext von ortino.CAM ist nicht öffentlich**, deshalb nimmt dieses Repository keinen Programmcode an. Es nimmt an, was ortino.CAM besser macht, ohne Code zu sein:

## Was willkommen ist

| Beitrag | Wie |
|---|---|
| **Test an einer echten Maschine** (am wertvollsten) | Issue-Vorlage »Test an einer echten Maschine«: Maschine, Steuerung und Firmware, Funktion, Ergebnis – auch Fehlschläge. Bitte zuerst ohne Werkzeug und Material testen. |
| **Fehlerbericht** | Issue-Vorlage »Fehler«: Version, was du getan hast, was passiert ist, was du erwartet hast; wenn möglich ein Projekt, das den Fehler zeigt (ohne persönliche Daten). |
| **Wunsch** | Issue-Vorlage »Wunsch«: welches Problem du lösen willst, nicht nur welche Funktion du dir vorstellst. |
| **Maschinenprofil** | Aus ortino.CAM exportieren (»Maschinen« → Exportieren), Datei ohne Höhenkarte und ohne persönliche Notizen als Pull Request unter `maschinenprofile/`. Nur Maschinen, die du selbst benutzt oder gut kennst; die Quelle der Maße im Pull Request nennen. |
| **Postprozessor-Vorlage** | TOML + Jinja unter `postprozessoren/`, mit einem kurzen Satz, auf welcher Steuerung du sie getestet hast. |
| **Beispielprojekte** | `.ocam`-Dateien unter `beispiele/`: eigene Arbeit, klein (unter 1 MB), mit einer Zeile, was sie zeigt. |
| **Übersetzungen, Anleitungen** | Korrekturen und neue Texte als Pull Request. |

**Fräsdesigns** (Schilder, Möbel, Muster …) gehören nicht hierher, sondern ins Community-Portal: im Programm über die Weltkugel in der Kopfleiste teilen.

## Regeln

* Nur **eigene Arbeit** oder Material, das du weitergeben darfst. Keine Dateien aus fremden Katalogen, keine Preislisten, keine Daten Dritter ohne Erlaubnis.
* **Keine persönlichen Daten** in Projekten, Profilen und Bildern (Namen, Adressen, Seriennummern, Zugangsdaten).
* Freundlich bleiben. Wer andere beleidigt oder belästigt, wird von den Issues und Pull Requests ausgeschlossen.
* Eine Änderung je Pull Request, mit kurzer Beschreibung.

## Rechte an deinem Beitrag

Mit einem Pull Request bestätigst du, dass der Beitrag von dir stammt, und räumst dem Betreiber von ortino.CAM ein **einfaches, zeitlich und räumlich unbeschränktes, unentgeltliches Recht** ein, ihn zu verwenden, zu verändern und mit ortino.CAM weiterzugeben (auch in der geschlossenen Programmfassung und im Portal). Deine Urheberschaft bleibt bei dir, und du darfst deinen Beitrag weiter selbst nutzen. Dateien in diesem Repository stehen unter denselben Bedingungen wie das Programm (`LICENSE`), soweit der Beitrag nichts anderes verlangt.

## Möchtest du am Programm selbst mitarbeiten?

Ja, gern. Schreibe ein Issue mit dem Titel »Mitarbeit am Programm« und beschreibe kurz, woran du Interesse hast und welche Erfahrung du mitbringst (Rust, TypeScript/React, CAM, GRBL, Tests, Doku). **Der Betreiber gibt Interessierten den Zugang zum privaten Entwicklungs-Repository frei** und bespricht mit dir Aufgabe, Arbeitsweise und Rechte, bevor du loslegst. Der Quelltext ist nicht öffentlich; wer Zugang bekommt, behandelt ihn vertraulich.
