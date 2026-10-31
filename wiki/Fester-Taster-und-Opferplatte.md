# Fester Taster und Opferplatte

Diese Seite gehört zu [Fräsen an der Maschine](Fräsen-an-der-Maschine). Sie erklärt zwei Hilfen für Maschinen mit fest eingebautem Werkzeugtaster: Der **feste Taster** misst die Länge jedes eingespannten Fräsers. Die **Höhenkarte** gleicht die Unebenheit der Opferplatte aus.

> **Ehrlich zum Stand:** Laut Rückmeldung des Betreibers (Ultimate Bee mit xPRO V5, Version 0.3.10) laufen an einer echten Maschine das **Einrichten des festen Tasters und das Einmessen eines Werkzeugs**. **Nur gegen den Simulator und automatische Tests geprüft** sind der Werkzeugwechsel am festen Taster mitten im Programm und die Messung der Opferplatte mit Höhenkarte, nie mit einer echten Opferplatte. Die Verdrahtungshinweise stammen vom Betreiber (Ultimate Bee mit xPRO V5) und sind nicht an der Hardware nachgeprüft. Lies vor dem Anschließen das Handbuch deiner Steuerung. Erste Messung ohne Material, Hand am Not-Aus.

Wenn dein Setup einfacher ist (Tastplatte, Werkzeugwechsel mit Pause), brauchst du diese Seite nicht.

## Begriffe

* **Opferplatte:** die Platte auf dem Maschinentisch, in die der Fräser beim Durchschneiden eintauchen darf. Sie schützt den Tisch.
* **Z-Null auf »Tisch (Opferplatte)«:** Alle Tiefen im Projekt zählen von der Oberfläche der Opferplatte aus. Das Werkstück oben ist dann genau so hoch wie seine Dicke. Einstellen kannst du das im Projekt (Schritt »Projekt«, Platteneinstellungen).
* **Fester Taster:** ein mechanischer Taster, der dauerhaft in der Maschine sitzt. Berührt ihn die Fräserspitze, löst er aus.
* **Höhenkarte:** eine Messung der Plattenhöhe an einem Raster von Punkten.

## Fester Taster

### Wie es funktioniert

Der Taster löst aus, wenn die Fräserspitze auf seiner Auslösefläche steht. Diese Fläche liegt eine feste Höhe über der Opferplatte. Löst irgendein Fräser aus, steht seine Spitze genau dort. Das Programm setzt Z-Null entsprechend, **ohne die Länge des Fräsers zu kennen**. Ein längerer Fräser löst früher aus und bekommt einen anderen Versatz.

Die Höhe der Auslösefläche bestimmst du **einmal** mit einem **Referenzfräser**: Opferplatte nullen (Spitze auf die Oberfläche, zum Beispiel mit einem Blatt Papier), dann die Spitze am Taster auslösen. **Opferplatte und Taster müssen mit demselben Fräser eingemessen werden.** Das Programm merkt sich den Namen des Referenzfräsers und warnt, wenn die Namen abweichen.

### Den Taster auswählen

* Ein mechanisch schaltender Taster mit **potentialfreiem Kontakt** (Öffner oder Schließer).
* **Kein Strom durch den Fräser.** Ein Taster, der den Fräser unter Spannung setzt, kann Spindel und Elektronik schädigen.
* Die Streuung zweier Messfahrten darf höchstens **0,5 mm** betragen, sonst bricht die Messung ab. Für saubere Ergebnisse sollte sie deutlich darunter liegen.
* Fest und spanfrei montiert, mit Platz zum Anfahren von oben, Kabel nicht im Weg des Fräsers.

Bei der xPRO V5 laut Angabe des Betreibers (nicht nachgeprüft): Der Probe-Anschluss ist ein dreipoliger Stecker. **SIG** und **GND** werden benutzt, der mittlere Pin bleibt frei. Schaltet der Taster »falsch herum«, kehrt eine Einstellung der Steuerung (`$6` bei GRBL, `$Probe/Invert` bei FluidNC) die Logik um. ortino.CAM zeigt dir die Zeile zum Kopieren, sendet sie aber nie.

### Einrichten (einmalig je Maschine)

In der Karte **Fester Taster** im Schritt »Fräsen«:

1. **Voraussetzungen:** verbunden, Referenzfahrt gemacht, Leerlauf, Taster-Eingang offen. Mit **»Taster-Eingang testen«** prüfst du, dass der Eingang beim Berühren schaltet und beim Loslassen zurückfällt. Referenzfräser einspannen, Spindel aus.
2. **Position:** Mit der Handsteuerung den Fräser über die **Mitte der Auslösefläche** fahren und »X/Y hier speichern«. Die **Annäherungshöhe** ist die Höhe, auf der die Maschine später in X/Y zum Taster fährt. Sie muss über Spannmitteln und Werkstück liegen. Den **Suchweg** (Standard 40 mm) wählst du großzügig, denn kürzere Werkzeuge lösen tiefer aus.
3. **Messen:** Die Maschine fährt über den Taster, tastet schnell (200 mm/min), zieht 2 mm zurück und tastet genau (40 mm/min).
4. **Höhe der Auslösefläche** über der Opferplatte: aus dem gespeicherten Z-Null der Opferplatte, aus dem aktuellen Z-Null der Steuerung oder von Hand eingetragen.
5. **Speichern:** Das Ergebnis liegt im Maschinenprofil (bei eigenen Maschinen auch in der Maschinenliste).

### Bei jedem Auftrag

1. Referenzfahrt.
2. Fräser einspannen und auf **»Werkzeug einmessen«** klicken. Die Maschine misst und legt Z-Null auf die Opferplatte.
3. X/Y-Nullpunkt am Werkstück von Hand setzen.
4. Im Projekt Z-Null auf **»Tisch (Opferplatte)«** stellen. Ab Version 0.3.11 ist das mit eingerichtetem festem Taster die Vorgabe für neue Projekte (umstellbar im Menü »Einstellungen« ▸ »Maschine & Z-Null …«); ein älteres Projekt stellst du mit dem Knopf **»Auf Opferplatte stellen«** in der Karte um. Steht es auf »Plattenoberseite«, warnt die Karte und fragt zweimal nach, denn das Programm würde sonst um die Materialdicke zu tief fräsen.
5. Start-Check, Lauf. Mit eingerichtetem festem Taster wechselt das Programm ab Version 0.3.12 **von selbst am Taster** (Werkzeugwechsel »Automatisch«); der Start-Check sagt, was gilt. Wer lieber mit Pause wechselt, klickt **»Stattdessen Pause«**. Eine ausdrücklich gespeicherte Wahl bleibt, wie sie war.

Beim Wechsel im Programm läuft es so: Anhalten, auf die Annäherungshöhe fahren, du wechselst und drückst »Weiter«, die Maschine misst das neue Werkzeug, setzt Z-Null und fährt zurück an die alte Stelle. Beide Werkzeuge stehen danach bei gleichem Werkstück-Z auf derselben Höhe über der Opferplatte (im Simulator mit Fräsern unterschiedlicher Länge geprüft).

Nach einem Lauf mit Wechsel gehört Z-Null zum **zuletzt gemessenen** Werkzeug. Beginnt der nächste Lauf wieder mit T1, spannst du T1 ein und klickst noch einmal auf **»Werkzeug einmessen«** – der Start-Check sperrt bis dahin (»Z-Null gehört zu einem anderen Werkzeug«). *Nur Simulator.*

### Sicherheit

* Nur nach Referenzfahrt. Ist der Taster-Eingang schon ausgelöst, sendet das Programm nichts.
* In X/Y fährt die Maschine **nur auf der Annäherungshöhe**, nie schräg.
* Das Programm schaltet die Spindel dabei **nie ein** und prüft nicht, ob sie läuft. Schalte sie vor dem Messen von Hand aus.
* Stopp geht jederzeit. Z-Null wird nie halb gesetzt: Es entsteht erst, wenn beide Messfahrten gültig waren.
* Findet der Taster keinen Kontakt im Suchweg, bleibt der Alarm stehen. Die Meldung nennt die Lösung (entsperren, Position und Kabel prüfen, neu messen).

Nach einem Stoß oder Umbau musst du den Taster neu einrichten. Die Streuprüfung fängt grobe Fehler ab, keine Verschiebung des Tasters.

## Opferplatte nullen und Höhenkarte

Eine Opferplatte ist nie ganz eben und verzieht sich mit der Feuchte. Eine Höhenkarte misst die Unebenheit **einmal**, speichert sie im Maschinenprofil und gleicht sie beim Fräsen aus: Die Fräserspitze folgt der Platte.

| Wichtig | Kaum nötig |
|---|---|
| Gravuren und flache Tiefen (0,1 bis 1 mm) | Taschen und Konturen, die tief genug schneiden |
| V-Carving und Inlays (die Tiefe bestimmt die Strichbreite) | Durchschnitte, bei denen die Opferplatte ohnehin angeschnitten wird |
| Große Werkstücke, bei denen die Platte um Zehntelmillimeter schwankt | Kleine Teile auf einer plangefrästen Platte |

### Bedienung

Schritt **Fräsen**, Karte **Opferplatte**. Voraussetzungen: verbunden, Referenzfahrt, Taster-Eingang offen, Platte frei.

1. **Nullen:** Die aktuelle X/Y-Stelle ist der Bezugspunkt. Entweder *Antasten mit Taster* oder *von Hand* (Spitze auf die Oberfläche, Papier dazwischen, dessen Dicke wird abgezogen). Trage den **Referenzfräser** ein. Ein neues Nullen verwirft die alte Höhenkarte.
2. **Raster wählen:** Bereich und Abstand (Vorgabe 50 mm, bei starker Welligkeit 25 mm). Das Programm zeigt Punktzahl und geschätzte Zeit. Höchstens 40 000 Punkte.
3. **Messen:** Je Punkt fährt die Maschine auf Sicherheitshöhe, tastet schnell, zieht zurück und tastet langsam. Fortschritt und Abbrechen sind jederzeit möglich.
4. **Ergebnis:** Eine Farbkarte (blau tief, orange hoch) zeigt Spanne und Streuung. »Speichern« legt die Höhenkarte ab.

Im Start-Dialog erscheint dann der Schalter **»Höhenkarte der Opferplatte anwenden«**.

### Wie der Ausgleich rechnet

* Der **exportierte G-Code bleibt unverändert**. Nur die Zeilen, die an die Steuerung gehen, werden beim Start umgerechnet.
* Bewegungen, die ganz über der Materialoberseite plus höchster Erhebung (plus 1 mm) verlaufen, bleiben unverändert.
* Alle anderen werden in kurze Stücke geteilt, damit die Spitze der Platte folgt.
* **Kreisbögen werden zu Geraden**, weil ein Bogen einer geneigten Fläche nicht folgen kann. Die Sehnen weichen höchstens 5 µm vom Bogen ab. Das bedeutet mehr Zeilen und eine etwas höhere Datenrate.

### Grenzen

* Gilt nur für Projekte mit Z-Null auf **»Tisch (Opferplatte)«**.
* Das Werkstück muss flach auf der Platte liegen. **Verzug des Werkstücks selbst erfasst die Höhenkarte nicht**, sie misst die Platte.
* Das Programm muss **ganz im vermessenen Bereich** liegen, sonst wird der Start abgelehnt.
* Nach 180 Tagen warnt der Start-Check, die Messung sei sehr alt. Nach Planfräsen, Tausch oder Verschieben der Platte ist sie ungültig. Markiere sie als veraltet und miss neu.
* Neu messen: nach Umbauten am Tisch oder an der Z-Achse, nach einem Wechsel des Tasters oder des Antastvorschubs und bei Gravuren nach großen Schwankungen von Feuchte oder Temperatur. Ein Stichprobentest mit Papier an zwei, drei Stellen hilft.
* Echte Firmware, echte Taster und echte Platten sind **nicht geprüft**. Das Planerverhalten bei sehr vielen kurzen Zeilen auch nicht.

## Mehr

* Das Planfräsen der Opferplatte (Bearbeitung »Planfräsen«) steht auf der Seite [Bearbeitungen](Bearbeitungen).
* Markierungen (Kreuz, Rahmen, Lineal, Anschlag-Linien, Lochraster) in die Opferplatte fräsen: [Opferplatte markieren](Opferplatte-markieren) (seit 0.4.1; die Tisch-Ansicht der Karte im Schritt »Fräsen« zeigt sie als geplant oder gefräst).
* Zurück zu [Fräsen an der Maschine](Fräsen-an-der-Maschine).

<!-- videos:start -->
## Videos (English)

* [![Plan marks for the spoilboard (video, English captions)](https://klapsc.github.io/ortino-cam/videos/spoilboard-marks-poster.jpg)](https://klapsc.github.io/ortino-cam/videos/#spoilboard-marks)  
**Plan marks for the spoilboard** · 14 s

Alle Videos: [Videos](Videos).
<!-- videos:end -->
