# Fehlersuche

Hier stehen häufige Probleme mit der Ursache und einer Lösung. Bei jedem Problem an der Maschine gilt: **Im Zweifel Not-Aus drücken, nicht erst »Stopp« in der Software.** Meldungen im Programm nennen meist selbst eine Lösung (»Lösung: …«). Lies sie zuerst. Findest du hier nichts, frag über [GitHub Issues](https://github.com/KlapSC/ortino-cam/issues/new/choose) (siehe [Mitmachen und Tests](Mitmachen-und-Tests)).

## Installation und Programm

| Problem | Ursache und Lösung |
|---|---|
| **Windows warnt beim Installieren** (SmartScreen) | Der Installer ist mit einem selbst erstellten Zertifikat signiert. Wenn du ihn von der offiziellen Release-Seite hast und die Prüfsumme stimmt: »Weitere Informationen« → »Trotzdem ausführen«. Siehe [Installation und Updates](Installation-und-Updates). |
| »3D-Ansicht nicht verfügbar« oder »WebGL ist nicht verfügbar« | Der Grafiktreiber stellt WebGL nicht bereit. Treiber aktualisieren, Hardwarebeschleunigung einschalten, ortino.CAM neu starten. Prüfliste und Auftragsübersicht funktionieren auch ohne. |
| Installation oder Update meldet, eine Datei könne nicht überschrieben werden | Meist hält Claude Desktop `ortino-mcp.exe` gesperrt. Claude Desktop beenden und erneut installieren. |
| Fehlertexte in der englischen Oberfläche sind deutsch | Bekannte Einschränkung (auch in 0.3.12): Meldungen des Kerns (Fehlertexte, Prüfliste) sind teils noch deutsch. |
| »Sicherung im Portal« meldet, das Portal sei zu alt, oder bietet sie nicht an | Die Sicherung braucht ein Portal ab Version 0.3.12. Der Betreiber des Portals muss den Server aktualisieren; bis dahin funktioniert alles andere wie bisher. Siehe [Sicherung im Portal](Sicherung-im-Portal). |
| Nach einem Absturz fehlt Arbeit | Beim Start bietet die Willkommensseite an, den automatisch gesicherten Stand wiederherzustellen. Speichere ihn danach unter einem Namen. |

## Verbindung zur Maschine

| Problem | Ursache und Lösung |
|---|---|
| **Kein COM-Anschluss in der Liste** | Steuerung einschalten, Kabel prüfen und »Anschlüsse aktualisieren«. Fehlt weiterhin etwas, fehlt der USB-Treiber (bei der xPRO V5 der CP210x von Silicon Labs, bei anderen Steuerungen oft CH340 oder FTDI). Bei der xPRO V5 funktioniert laut Herstellerangabe ein Kabel von USB-C auf USB-C nicht, nimm USB-A auf USB-C. |
| **Keine Antwort nach dem Verbinden** | Falsche Baudrate (GRBL-Standard und xPRO V5: 115200) oder die Steuerung startet noch neu. Beim Öffnen des Anschlusses startet die xPRO V5 neu, die Meldung `Grbl …` in der Konsole ist normal. Erneut verbinden. |
| Statusleiste: **»Keine Antwort seit … s«** | Kabel und Stromversorgung prüfen, nötigenfalls trennen und neu verbinden. Nach 8 Sekunden Stille während eines Auftrags hält das Programm den Vorschub an. |
| **Verbindung bricht mitten im Auftrag ab** | Häufigste Ursache ist das USB-Energiesparen von Windows. In den Energieoptionen das »selektive USB-Energiesparen« deaktivieren, im Geräte-Manager bei den USB-Hubs und beim COM-Anschluss »Computer kann das Gerät ausschalten …« abwählen, Ruhezustand während langer Aufträge abschalten, USB-Kabel kurz halten und getrennt von Motor- und Spindelleitungen führen. Nach einem Abbruch zeigt ein Hinweis die letzte bestätigte Zeile und bietet »Start ab Zeile« an. Prüfe vorher Referenzfahrt und Nullpunkt. |
| Netzwerk-Verbindung klappt nicht | Adresse als `Adresse:Port` eintragen (zum Beispiel `192.168.1.50:23`). |

## Alarm, Referenzfahrt und Fahrtrichtung

| Problem | Ursache und Lösung |
|---|---|
| **Alarm** in der Karte | Die Steuerung ist gesperrt. Ursache beheben, dann **Entsperren (`$X`)**, **Referenzfahrt (`$H`)** oder **Zurücksetzen**. **Nach einem Alarm kann die Position verloren sein.** Prüfe den Nullpunkt, bevor du fräst. |
| Ein Alarm hat den Auftrag angehalten | Weiterfahren geht nicht, weil die Steuerung Spindel und Absaugung abgeschaltet und den Puffer verworfen hat. Auftrag abbrechen, Nullpunkt und Werkzeug prüfen, dann mit »Start ab Zeile« neu starten. |
| Alarm 2 (Soft-Limit) mitten im Auftrag | Eine Fahrt hätte den Verfahrweg überschritten. Der Start-Check prüft das vorab. Lies seine Fehler, und prüfe Verfahrwege im Maschinenprofil und `$130–$132` ([Maschine einrichten](Maschine-einrichten)). |
| Referenzfahrt fährt in die falsche Ecke | `$23` (Richtung) und `$3` (Achsrichtung) prüfen. Der Einrichtungsassistent leitet die Ecke aus `$23` ab. |
| Eine Achse fährt verkehrt herum | Achsentest im Assistenten, Maske `$3` ändern oder das Motorkabel der Achse umpolen. Richtig ist +X nach rechts, +Y nach hinten, +Z nach oben. |
| Die Handsteuerung fährt nicht | Sie ist gesperrt, solange die Maschine nicht bereit ist (Alarm, nicht im Leerlauf) oder ein Programm läuft. Der Grund steht in der Karte. |
| »Start gesperrt« | Der Start-Check hat Fehler gefunden (zum Beispiel keine Referenzfahrt, Verfahrweg überschritten, Alarm, Prüfliste mit Fehlern). Fehler lassen sich nicht wegklicken, behebe sie. Warnungen bestätigst du einzeln mit »Verstanden«. |

## Nullpunkt und Antasten

| Problem | Ursache und Lösung |
|---|---|
| **Antasten schlägt fehl:** »kein Kontakt« (Alarm 5) | Der Fräser hat im Suchweg nichts berührt. Prüfe, ob die Klemme am Fräser sitzt, das Kabel am Taster-Eingang steckt und die Tastplatte oder der Eckblock sauber ist. Mit **»Taster-Eingang testen«** prüfst du Kabel und Kontakt. Vergrößere ggf. die »Max. Tiefe«. Dann entsperren (`$X`) und neu antasten. Der Nullpunkt bleibt dabei unverändert. |
| Antasten: **Alarm 4**, Taster schon ausgelöst | Der Taster-Eingang meldet schon vor dem Start Kontakt. Fräser abheben, Klemme und Kabel prüfen (Kurzschluss?). Antasten bleibt gesperrt, bis der Eingang offen ist. |
| Die Anzeige »Taster-Eingang« bleibt »unbekannt« | Manche Firmware meldet den Pin-Zustand nicht. Dann bleibt nur die Luftprobe mit dem Antasten selbst. |
| Antasten gesperrt: Materialdicke unbekannt | Steht Z-Null auf »Tisch (Opferplatte)«, braucht die Karte die Materialdicke. Prüfe die Dicke in den Platteneinstellungen im Schritt »Projekt«. Das Programm rät nicht. |
| **Das Werkstück wird zu tief oder gar nicht gefräst** | Prüfe Z-Null: **Plattenoberseite** oder **Tisch (Opferplatte)** im Projekt, dazu die Dicke der Tastplatte (liegt sie auf Werkstück oder Opferplatte?). Fahre vorher einen **Luftschnitt** und prüfe Z0 mit einem Blatt Papier: Nach dem Setzen von Z0 muss der Fräser auf der Oberfläche stehen. |
| X/Y-Nullpunkt liegt an der falschen Ecke | Beim Eckblock die Ecke in der Karte passend zum Nullpunkt der Platte wählen (der Hinweis in der Karte warnt). Mitte als Nullpunkt lässt sich mit dem Eckblock nicht antasten. |

## Maße und Werkzeugwege

| Problem | Ursache und Lösung |
|---|---|
| **Maße stimmen nicht** (Teil zu groß oder zu klein) | Mehrere Ursachen: (1) **Import** mit falschem Maßstab. Bei SVG gilt 1 px = 0,2646 mm (96 dpi), bei Dateien aus Programmen mit 72 dpi hilft die Schnellwahl »72 → 96 dpi ×1,33«. (2) **Schritte pro Millimeter** der Steuerung: Probe 100 mm fahren und nachmessen, `$100–$102` prüfen. (3) **Zoll-Berichte** (`$13=1`) verfälschen Positionen um 25,4. (4) **Fräserdurchmesser** im Projekt weicht vom echten ab. |
| Verbindungen (Zinken, Schlitze) passen nicht | Miss die echte Dicke und fräse den **Testcoupon**, siehe [Platten und Möbel](Platten-und-Möbel). Materialquellung und Fräserverschleiß kennt das Programm nicht. |
| **»Werkzeugweg nicht berechenbar«** | Die Meldung nennt die Ursache und eine Lösung. Häufig: keine Formen zugewiesen (»Auswahl übernehmen«), Tasche auf einer **offenen** Form (Pfad schließen oder verbinden), Endtiefe nicht tiefer als Starttiefe, Zustellung 0, unbekannte Variable (unter »Projekt → Variablen« anlegen), Form auf einer anderen Platte oder ein ungültiges Werkzeug (unter »Werkzeuge verwalten« korrigieren). |
| Bahnen fehlen oder die Bearbeitung zeigt »leer« | Die Geometrie-Prüfung zeigt offene oder doppelte Konturen, Selbstschnitte und zu enge Innenradien. Beim V-Carving ist ein Ausräumwerkzeug evtl. zu groß für den Flachboden, die Meldung nennt eine Tiefe als Ausweg. |
| Bahnen sehen **falsch** aus: Der Fräser schneidet innen statt außen | Prüfe bei einem Profil die **Seite** (Außen, Innen, Auf Linie). Außen heißt: Das Teil innerhalb der Kontur behält seine Größe. |
| Innenecken werden rund | Ein runder Fräser kann keine scharfe Innenecke fräsen. Nutze Innenecken freistellen (Dogbone), einen kleineren Fräser oder rechne das ein. |
| Teile lösen sich beim Durchschneiden oder fliegen weg | Haltestege fehlen. Die Prüfliste und die Hinweise melden das für Durchschnitte. |
| **Kante rau oder verbrannt** | Vorschub und Drehzahl prüfen (es sind Richtwerte!). Bei Holz oder Kunststoff kann **Gleichlauf** sauberer sein, siehe [Bearbeitungen](Bearbeitungen). Der Hinweis »Span zu dünn (Brandgefahr)« schlägt den Richtwert vor. Hast du für den Fräser eine Standzeit-Grenze gesetzt, meldet der Start-Check, wenn sie erreicht ist ([Werkzeuge und Schnittdaten](Werkzeuge-und-Schnittdaten)). |
| Export gesperrt | Die Prüfliste hat **Fehler**. Fehler lassen sich nicht akzeptieren, Warnungen schon. Lies die Lösung am Eintrag. |
| Eilgang fährt in stehendes Material | Die Prüfliste meldet das als Fehler. Lege davor eine Bearbeitung an, die bis zu dieser Tiefe räumt, oder setze die Starttiefe auf 0. |

## Kamera auf der Arbeitsplatte

| Problem | Ursache und Lösung |
|---|---|
| **Die Kamera findet die Marken nicht** | (1) Marken im Bild zu klein: näher heran, höhere Auflösung oder größere Marken (bis 100 mm). (2) Verrauscht, unscharf oder spiegelnd: gleichmäßiges, weiches Licht, matt gedruckte Marken, kein Gegenlicht. (3) Marken am Bildrand abgeschnitten: Kamera so ausrichten, dass alle vier ganz im Bild liegen. (4) Mindestens drei Marken müssen brauchbar sein, vier sind besser. (5) Das Blatt wurde nicht mit 100 % gedruckt: Prüfe den 100-mm-Maßstab. (6) Marken verschiedener Blätter oder doppelt: ein Blatt, jede Nummer einmal. |
| »Zuordnung nicht eindeutig« | Das Programm rät nicht. Häufig ist das Bild gespiegelt, oder die Marken liegen nicht in den Ecken. |
| Das Bild passt nicht zum Entwurf | Parallaxe: Die Marken müssen auf Höhe der Materialoberfläche liegen. Wurde die Kamera angestoßen, neu kalibrieren. |
| Das Kamera-Symbol fehlt in der Kopfleiste | In schmalen Fenstern (unter 1180 Pixeln Breite) entfällt das Symbol, damit es den Schritt »Fräsen« nicht überlappt. Die Kamera bleibt über `Strg+K`, die Werkzeugpalette im Schritt »Design« und die Statusleiste erreichbar. |
| Der Zugriff auf die Kamera wird verweigert | **Einstellungen → Datenschutz & Sicherheit → Kamera:** Kamerazugriff, »Apps den Zugriff auf Ihre Kamera erlauben« und »Desktop-Apps …« einschalten. Das ist unter Windows noch nicht geprüft. Mit »Bild aus Datei …« geht es auch ohne Kamera. |

Mehr dazu auf [Kamera auf der Arbeitsplatte](Kamera-auf-der-Arbeitsplatte).

## Handy, Claude und Portal

* **Handy-Fernbedienung:** Siehe die Tabelle »Wenn es nicht klappt« auf [Handy-Fernbedienung](Handy-Fernbedienung) (Firewall, gleiches WLAN, Code abgelaufen, Verbindung unruhig).
* **Claude erscheint nicht in Claude Desktop:** Siehe [Claude, MCP und API](Claude-MCP-und-API).
* **Portal:** »Keine Verbindung zum Portal …« und weitere Meldungen stehen mit Lösung unter [Community-Portal](Community-Portal). ortino.CAM arbeitet ohne Portal normal weiter.

## Nichts davon hilft?

Melde es als Issue. Nenne Version, Windows-Version, was du getan hast und was du erwartet hast. Bei Problemen an der Maschine nenne Maschine und Steuerung und hänge den Auszug aus der Konsole an. Bitte **keine persönlichen Daten**. Sicherheitslücken meldest du **nicht** als öffentliches Issue (siehe [Sicherheitsrichtlinie](https://github.com/KlapSC/ortino-cam/blob/main/SECURITY.md)).
