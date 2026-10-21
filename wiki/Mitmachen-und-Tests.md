# Mitmachen und Tests

**Neue Mitwirkende sind willkommen.** Der Quelltext von ortino.CAM ist nicht öffentlich, mitmachen kannst du trotzdem an vielem. Am wertvollsten sind **Tests an echten Maschinen**, denn ortino.CAM entsteht zum größten Teil mit Claude Code (Anthropic) als Co-Autor. Tausende automatische Tests prüfen die Rechnung, aber sie stammen aus derselben Quelle wie der Code. Nur ein Test an einer echten Maschine zeigt, ob etwas wirklich funktioniert.

Die ausführlichen Regeln stehen in der [CONTRIBUTING.md](https://github.com/KlapSC/ortino-cam/blob/main/CONTRIBUTING.md). Kontakt gibt es **ausschließlich über [GitHub Issues](https://github.com/KlapSC/ortino-cam/issues/new/choose)**.

## Was willkommen ist

| Beitrag | Wie |
|---|---|
| **Test an einer echten Maschine** (am wertvollsten) | Issue-Vorlage »Test an einer echten Maschine«. Auch Fehlschläge helfen. |
| **Fehlerbericht** | Issue-Vorlage »Fehler« |
| **Frage** | Issue-Vorlage »Frage« |
| **Wunsch** | Issue-Vorlage »Wunsch«. Beschreibe, welches Problem du lösen willst, nicht nur welche Funktion du dir vorstellst. |
| **Maschinenprofil** | Aus dem Programm exportieren und als Pull Request ablegen |
| **Postprozessor-Vorlage** | TOML und Jinja als Pull Request |
| **Beispielprojekt** | `.ocam`-Datei als Pull Request |
| **Übersetzungen und Anleitungen** | Korrekturen und neue Texte als Pull Request. Fehler im Wiki meldest du als Issue. |
| **Mitarbeit am Programm** | Issue mit dem Titel »Mitarbeit am Programm« |

**Fräsdesigns** (Schilder, Möbel, Muster …) gehören nicht hierher, sondern ins [Community-Portal](Community-Portal). Teile sie am besten direkt aus dem Programm.

## So meldest du einen Test an einer echten Maschine

Bitte teste **zuerst ohne Werkzeug und ohne Material**, mit dem Not-Aus in Reichweite und mit den Hinweisen aus [Fräsen an der Maschine](Fräsen-an-der-Maschine). Dann:

1. Öffne ein neues Issue und wähle die Vorlage **»Test an einer echten Maschine«**.
2. Fülle die Felder aus:
   * **Version von ortino.CAM** (im Dialog »Über ortino.CAM«),
   * **Maschine und Steuerung** mit Firmware, zum Beispiel »Ultimate Bee 1000, CNC xPRO V5, GRBL 1.1h«,
   * **Was hast du getestet?** Zur Wahl stehen: Fester Taster (Werkzeug einmessen, Wechsel-Assistent), Opferplatte nullen und Höhenkarte, Tastplatte und Eckblock (Antasten), Wechsel-Assistent mit Längensensor, Handy-Fernbedienung, An Position fahren, Maschinenprofil oder Anderes,
   * **Ergebnis:** hat wie beschrieben funktioniert, funktioniert mit Einschränkungen, hat nicht funktioniert, oder die Maschine hat unerwartet reagiert,
   * **Was ist passiert?** Beschreibe den Ablauf, die Meldungen des Start-Checks und füge einen Auszug aus der **Konsole** der Maschine ein (im Schritt »Fräsen« die Karte »Konsole«, die Zeilen mit `tx` und `rx`).
3. **Keine persönlichen Daten**: keine Namen, Adressen, Seriennummern und keine Zugangsdaten in Berichten, Projekten oder Bildern.

Auch ein Bericht, in dem **nichts funktioniert hat**, hilft. Ein Bericht, dass etwas funktioniert hat, hilft genauso, denn so wird aus »nur im Simulator geprüft« irgendwann »erprobt«.

### Was besonders gebraucht wird

Nur an der **Ultimate Bee mit xPRO V5** sind bisher erprobt: Taschen, V-Carving, Konturen, Referenzfahrt und Werkzeugwechsel mit der Tastplatte (Version 0.3.3). Alles Folgende ist **nur gegen den Simulator, Tests oder erzeugte Bilder geprüft** und wartet auf deinen Bericht:

* fester Taster, Messung der Opferplatte und Höhenkarte,
* Handy-Fernbedienung (mit echtem Handy im echten WLAN),
* »An Position fahren«, Wechsel-Assistent mit Längensensor, Antasten mit dem Eckblock, Absaugung,
* Rahmen fahren, Luftschnitt, Pause und Start ab Zeile (an der echten Maschine nicht einzeln bestätigt),
* Gewindefräsen, Wartungsplan und Standzeit-Grenzen,
* die Kamera auf der Arbeitsplatte (mit einer echten Kamera),
* die neuen Postprozessoren (UCCNC, Centroid, ShopBot, MASSO, PlanetCNC) und andere Steuerungen als die xPRO V5,
* gefräste Passungen, Fingerzinken, Inlays, Reliefs und Möbelteile.

## Beiträge als Dateien (Pull Request)

Für Dateien legst du einen **Pull Request** im [öffentlichen Repository](https://github.com/KlapSC/ortino-cam) an. Eine Änderung je Pull Request, mit kurzer Beschreibung.

* **Maschinenprofil:** Im Programm unter »Maschinen« das Profil wählen und **Exportieren**. Die Datei darf **keine Höhenkarte und keine persönlichen Notizen** enthalten. Lege sie unter `maschinenprofile/` ab, Dateiname `hersteller-modell-steuerung.json` (zum Beispiel `ultimate-bee-1000-xpro-v5.json`). Nenne im Pull Request die Quelle der Maße und ob du die Maschine selbst benutzt. Nur Maschinen, die du selbst benutzt oder gut kennst.
* **Postprozessor-Vorlage:** TOML und Jinja unter `postprozessoren/`, mit einem Satz, **auf welcher Steuerung und Firmware du sie getestet hast** und wie (an der Maschine oder nur die Ausgabe geprüft). Siehe [Postprozessoren und Steuerungen](Postprozessoren-und-Steuerungen).
* **Beispielprojekte:** `.ocam`-Dateien unter `beispiele/`, eigene Arbeit, klein (unter 1 MB), mit einer Zeile, was sie zeigen.

### Regeln und Rechte

* Nur **eigene Arbeit** oder Material, das du weitergeben darfst. Keine Dateien aus fremden Katalogen, keine Preislisten, keine Daten Dritter ohne Erlaubnis.
* **Keine persönlichen Daten** in Projekten, Profilen und Bildern.
* Bleib freundlich. Wer andere beleidigt oder belästigt, wird von den Issues und Pull Requests ausgeschlossen.
* Mit einem Pull Request bestätigst du, dass der Beitrag von dir stammt, und räumst dem Betreiber ein einfaches, zeitlich und räumlich unbeschränktes, unentgeltliches Recht ein, ihn zu verwenden, zu verändern und mit ortino.CAM weiterzugeben (auch in der geschlossenen Programmfassung und im Portal). Deine Urheberschaft bleibt bei dir, und du darfst deinen Beitrag weiter selbst nutzen. Maßgeblich ist der Wortlaut in der CONTRIBUTING.md.

## Mitarbeit am Programm

Wenn du am Programm selbst mitarbeiten möchtest, schreibe ein Issue mit dem Titel **»Mitarbeit am Programm«**. Beschreibe kurz, woran du Interesse hast und welche Erfahrung du mitbringst (Rust, TypeScript und React, CAM, GRBL, Tests, Dokumentation). Der Betreiber gibt Interessierten den Zugang zum privaten Entwicklungs-Repository frei und bespricht mit dir Aufgabe, Arbeitsweise und Rechte, bevor du loslegst. Wer Zugang bekommt, behandelt den Quelltext vertraulich.

## Sicherheitslücken

Melde Sicherheitslücken **nicht** als öffentliches Issue. Im Reiter **Security** des Repositorys gibt es »Report a vulnerability« (ein privater Bericht an den Betreiber). Besonders wichtig sind Lücken in der Handy-Fernbedienung, im Updater, in der Maschinenanbindung und in der Verarbeitung fremder Dateien. Wenn ein Fehler dazu führen kann, dass die Maschine unerwartet fährt, melde ihn **dringend** und beschreibe die Bedingungen. Mehr in der [Sicherheitsrichtlinie](https://github.com/KlapSC/ortino-cam/blob/main/SECURITY.md).

## English

ortino.CAM is closed source, but you can still help in many ways. The most valuable contribution is a **test report from a real machine**, including failures. Use the issue template "Test an einer echten Maschine" (test on a real machine), and test without tool and material first, with the emergency stop within reach. Machine profiles, post-processor templates, example projects, translations and guides are welcome as pull requests with data files only (see the CONTRIBUTING.md in the repository). Milling designs belong in the community portal, and contact is through GitHub issues only. The software is provided as is, without warranty.
