# Werkzeuge und Schnittdaten

Welcher Fräser, wie schnell, wie tief? Diese Seite erklärt die **Fräserbibliothek**, die **Richtwerte** für Vorschub und Drehzahl, die **bewährten Schnittdaten**, die du selbst speichern kannst, und die **Standzeit-Grenzen**.

> **Ehrlich zum Stand:** Alle Schnittwerte im Programm sind **Richtwerte**. Sie werden aus Material, Fräserdurchmesser, Schneidenzahl und den Grenzen deiner Maschine gerechnet und sind **nicht an einer echten Maschine nachgemessen**. Sie hängen von deiner Maschine, deinem Fräser und deinem Material ab. Prüfe sie, fange vorsichtig an und probiere an einem Reststück. Die Katalogmaße der Fräser stammen nicht aus Datenblättern (siehe unten). Standzeit-Grenzen und Wartungsintervalle sind **nur gegen den Simulator geprüft** und keine Herstellervorgabe.

## Werkzeuge im Projekt

Jedes Projekt hat seine **Werkzeugliste**. Jede Bearbeitung nutzt ein Werkzeug daraus. Ein Werkzeug hat Art (Schaftfräser, Kugelfräser, V-Fräser, Bohrer, Gravierstichel, Gewindefräser …), Maße, Schneidenzahl und Richtwerte für Drehzahl, Vorschub, Eintauchvorschub, Zustellung und Bahnabstand. Du verwaltest sie im Werkzeug-Dialog (»Werkzeuge verwalten«). Das Programm kennt Standardwerkzeuge: Schaftfräser von 3,175 bis 6,35 mm, einen Kugelfräser, V-Fräser, einen 3-mm-Bohrer, einen Gravierstichel und einen Gewindefräser. Fehlt eines davon, fügen es die Assistenten (zum Beispiel der Schnellstart) bei Bedarf dem Projekt hinzu.

## Die Fräserbibliothek

Die Bibliothek enthält über 250 Fräser von elf Herstellern (unter anderem Amana, SpeTool, Whiteside, Onsrud, Yonico, IDC Woodcraft, Bits & Bits, Sienci Labs, Inventables, Carbide 3D, Genmitsu). Öffnen kannst du sie über die Befehlspalette (`Strg+K`: »Fräser-Bibliothek öffnen …«), den Werkzeug-Dialog oder die Fräserwahl einer Bearbeitung (»Aus der Fräser-Bibliothek wählen …«).

**Suchen:** Das Suchfeld verzeiht Tippfehler und liest Maße: `6mm`, `1/4`, `0,25in`, `60°`. Beispiele: »kompresion 6mm«, »60° v«, »ball 1/8«. Filter gibt es für Hersteller, Typ, Schnittrichtung, Durchmesser, Schneidenlänge, Schaft, Schneidenzahl, Winkel, Material und mehr. Die Schnellwahl **»für Platte ≥ Dicke + 0,3«** zeigt nur Fräser, die lang genug zum Durchschneiden sind. Du kannst zwei bis drei Fräser vergleichen und Favoriten markieren.

**Auswahlhilfe:** Du gibst Aufgabe (Kontur, Tasche, V-Carving, Gravur, Inlay, Planen, Bohren, 3D-Relief, Fase), Material, Plattendicke und kleinste Einzelheit an, und das Programm schlägt Fräser vor, jeweils **mit Begründung**. Das sind Faustregeln, keine Garantie. Zum Beispiel muss die Schneide beim Durchschneiden länger als Tiefe plus 0,3 mm sein, für 18 mm Birkensperrholz also mindestens 18,3 mm. Der Durchmesser darf nie größer sein als die kleinste Einzelheit. Für Sperrholz, Melamin und Hartholz kommt eher ein Kompressionsfräser infrage, für Kunststoff und Aluminium ein Einschneider, für feinen Text ein 60°-V-Fräser. Ist nichts passend, sagt das Programm warum und was du lockern kannst.

### Wie verlässlich sind die Katalogdaten?

Die Katalogeinträge stammen aus **Suchergebnistexten** der Hersteller- und Händlerseiten (Stand Oktober 2026). Die Originalseiten und Datenblätter waren dabei nicht abrufbar, und niemand hat die Fräser nachgemessen.

| Kennzeichnung | Bedeutung |
|---|---|
| **Geprüft** | Die Maße standen im Text der Quelle ausdrücklich so da und sind plausibel. Es heißt **nicht**, dass jemand nachgemessen hat. |
| **Abgeleitet** | Aus einer Serientabelle oder berechnet (zum Beispiel die Schneidenlänge eines V-Fräsers aus Durchmesser und Winkel). |
| **Ungeprüft** | Die Quelle war widersprüchlich oder unvollständig. Der Grund steht in der Notiz. |
| **Eigen** | Dein eigener Eintrag. |

**Prüfe die Maße vor dem Kauf beim Hersteller.** Jeder Eintrag hat einen Quell-Link (»Link kopieren«). Es gibt keine Preise. Es fehlen zum Beispiel metrische 6-mm-Langschneider und einige Marken, für die sich nichts Verlässliches finden ließ (QWOCA, Drillman, Vortex, Stepcraft, Sorotec, CNC-Step, Onefinity). Chip-Load-Tabellen von Herstellern sind **nicht** enthalten.

### Eigene Fräser

Unter **Meine Bibliothek** trägst du die Fräser ein, die du wirklich hast: Bauart, Durchmesser und Schneidenlänge sind Pflicht, alles andere freiwillig. Fehlende Angaben schätzt das Programm und meldet sie (»bitte nachmessen«). Du kannst Einträge bearbeiten, duplizieren und löschen. Mit **Sichern (Export JSON)** und **Wiederherstellen** nimmst du deine Bibliothek auf einen anderen PC mit. Vorhandene Fräser werden dabei nie überschrieben. Die Bibliothek ist die Datei `tools.json` im Datenverzeichnis (unter Windows `%APPDATA%\ortino.CAM`).

### Import und Export

Du kannst Fräserlisten aus anderen Programmen einlesen: **Vectric** (`.vtdb`), **Fusion 360** (`.json`, `.tools`), **CSV** (Spaltenzuordnung in der Vorschau änderbar), **LinuxCNC** (`.tbl`) und den eigenen JSON-Export. Vor dem Übernehmen siehst du eine Vorschau (neu, Duplikat, Fehler). Es wird nie etwas überschrieben. Exportieren kannst du als CSV, JSON oder Fusion-360-JSON.

> **Grenzen:** Das `.vtdb`-Format ist nicht offiziell dokumentiert und wurde **mit einer echten Vectric-Datei nicht getestet**. Das Fusion-Format ist ebenfalls nicht mit echten Dateien geprüft, und der Fusion-Export wurde nicht in Fusion geladen.

## Richtwerte für Vorschub und Drehzahl

Wenn du ein Werkzeug wählst, zeigt das Programm Schnittwerte als Vorschlag: Drehzahl, Vorschub, Eintauchvorschub, Zustellung je Durchgang und Bahnabstand. Sie entstehen so:

* Grundwert aus Material, Durchmesser und Schneidenzahl,
* Faktoren für die **Werkstoffgruppe** (Weichholz, Hartholz, Sperrholz, MDF, Acryl, Kunststoff, Hartschaum, Aluminium) und die **Holzart** (29 Holzarten, Platten und Kunststoffe mit Härteklasse),
* Faktoren für die **Fräserbauart** (zum Beispiel Abwärtsspirale oder Schruppfräser),
* **Spanausdünnung:** Bei schmalem seitlichem Eingriff wird der Vorschub erhöht, damit der Span nicht zu dünn wird (höchstens auf das Doppelte),
* Begrenzung auf die Grenzen deiner Maschine (Höchstvorschub, Drehzahlbereich, 80 % der Spindelleistung, wenn bekannt).

**»Warum dieser Vorschub?«** zeigt dir jeden Schritt mit Faktor und Wert. Im Einfach-Modus steht eine verständliche Zeile wie »Schnittwerte vom Fräser: 2880 mm/min bei 18000 U/min«. Die Faktoren der Werkstoffdatenbank sind **Annahmen** (Einordnung nach Härte und üblicher Werkstattpraxis), nicht gemessen. Härtewerte, die im Programm stehen, dienen nur der Anzeige. Die Hinweise des Programms warnen, wenn ein Vorschub weit über dem Richtwert liegt (»Vorschub weit über dem Richtwert«), der Span zu dünn wird (»Brandgefahr«) oder die Zustellung zu tief ist.

## Meine bewährten Schnittdaten

Lief ein Projekt gut, kannst du die Werte dieser Bearbeitung als **bewährt** merken: Vorschub, Drehzahl, Eintauchvorschub, Zustellung und Seitenzustellung. Künftige Vorschläge und neue Bearbeitungen nehmen sie dann bevorzugt, mit der Herkunft (»bewährt, 3-mal bestätigt, zuletzt …«). Der Richtwert bleibt zum Vergleich daneben stehen.

* Ein Eintrag gilt für **Werkzeug + Material (+ Bearbeitungsart)**. Dasselbe Werkzeug in einem anderen Projekt wird wiedererkannt.
* Speichern: im Eigenschaften-Panel der Bearbeitung (Abschnitt »Vorschub & Drehzahl«) auf **»Als bewährt speichern«**, oder nach einem Lauf über den Hinweis »Lief es gut? Schnittdaten als bewährt speichern«.
* Ansehen, bearbeiten, löschen: Werkzeug-Dialog → **»Meine Schnittdaten«**.
* **Maschinengrenzen gelten immer:** Bewährte Werte werden an die Grenzen der Maschine des Projekts gekappt, und das Programm meldet es.
* Das Programm **lernt nichts von selbst**. Ein Eintrag entsteht nur, wenn du ihn speicherst. Die Werte sind deine Erfahrung an **deiner** Maschine mit deinem Material und werden nicht geprüft und nirgends hin übertragen. Der Material-Abgleich ist genau: Ein Eintrag für `plywood` gilt nicht für `birch_plywood`.

## Standzeit-Grenzen und Wartungsplan

Das **Job-Protokoll** hält fest, was du wirklich gefräst hast: ein Eintrag je Programmlauf mit geschätzter und tatsächlicher Zeit (ohne Pausen und Wartezeit im Werkzeugwechsel), Ergebnis und Werkzeugen. Es liegt nur lokal auf deinem Rechner, enthält nie G-Code oder Pfade und verlässt den Rechner nie. Rahmen fahren und Antasten werden nicht protokolliert. Daraus entstehen:

* **Zeitkalibrierung:** Nach mindestens drei abgeschlossenen Läufen von je mindestens fünf Minuten zeigt der Start-Dialog »nach deinen bisherigen Läufen etwa …«. Im Rüstblatt kannst du die Zeitschätzung damit kalibrieren (Standard aus, siehe [Rüstblatt und Angebot](Rüstblatt-und-Angebot)). Der Faktor ist ein Median über wenige Läufe, kein Versprechen.
* **Standzeit-Grenze je Werkzeug:** Im Werkzeugdialog trägst du eine Grenze in **Minuten Schnittzeit** ein. Das Programm zählt die Schneidzeit seit dem letzten Zurücksetzen. Der Start-Check weist ab 80 % der Grenze darauf hin und warnt, wenn der Lauf die Grenze überschreiten würde. Nach einem Fräserwechsel oder dem Schärfen klickst du auf »Standzeit zurücksetzen«. Es gibt keine Materialfaktoren: Wer harte Werkstoffe fräst, setzt die Grenze niedriger. Luftschnitte zählen nicht.
* **Wartungsplan je Maschine:** Im Job-Protokoll gibt es den Reiter **»Wartung«**. Punkte wie Spindel, Schmierung, Opferplatte oder Filter bekommen ein Intervall in Betriebsstunden, Kalendertagen oder Läufen. Fällige Punkte meldet der Start-Check (Hinweis ab 90 % des Intervalls, Warnung wenn überfällig). Mit »Erledigt« setzt du den Zähler zurück.

Die Zeit je Werkzeug ist eine Näherung (sie richtet sich nach der zuletzt von der Steuerung bestätigten Zeile und kann an Werkzeugwechseln um einige Sekunden abweichen). Grenzen und Intervalle sind **Richtwerte ohne Messung und ohne Herstellervorgabe**.

## Weiter

* [Bearbeitungen](Bearbeitungen)
* [Prüfen und Simulation](Prüfen-und-Simulation)
* [Rüstblatt und Angebot](Rüstblatt-und-Angebot)
