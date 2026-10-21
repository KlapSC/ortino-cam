# Prüfen und Simulation

Bevor du fräst, prüft ortino.CAM dein Projekt auf mehreren Ebenen. Im Schritt **Prüfen** siehst du die **Prüfliste**, die **3D-Simulation** und eine Zeitschätzung. Dazu kommen die **Hinweise** (die Glühbirne in der Kopfleiste) und später an der Maschine der **Start-Check**.

![3D-Simulation des Materialabtrags mit Prüfliste und Vorschlägen](https://raw.githubusercontent.com/KlapSC/ortino-cam/main/docs/bilder/simulation-light.png)

> **Wichtig:** Simulation, Prüfliste, Hinweise und Start-Check sind **Hilfen und keine Sicherheitsfunktion**. Sie können Fehler übersehen. Sie ersetzen weder den Not-Aus noch eine Schutzeinrichtung noch deine eigene Sorgfalt. Prüfe Werkzeugwege, Nullpunkt, Werkzeug und Einspannung vor jedem Lauf selbst, teste zuerst **ohne Werkzeug und Material** und lass die Maschine nie unbeaufsichtigt. Siehe den [Haftungsausschluss](https://github.com/KlapSC/ortino-cam#haftungsausschluss).

## Die vier Prüfebenen im Überblick

| Ebene | Wo | Was sie leistet |
|---|---|---|
| **Geometrie-Prüfung** | Design | Findet Probleme in deinen Zeichnungen, bevor Werkzeugwege entstehen. |
| **Prüfliste** | Schritt »Prüfen« | Prüft die berechneten Werkzeugwege. **Fehler sperren G-Code-Export und Maschinenstart.** |
| **Hinweise** | Glühbirne in der Kopf- und Statusleiste | Schlagen Verbesserungen vor, sperren nie etwas. |
| **Start-Check** | Schritt »Fräsen« | Vergleicht den Zustand der Steuerung mit dem Projekt. Siehe [Fräsen an der Maschine](Fräsen-an-der-Maschine). |

## Die Prüfliste

Die Prüfliste zeigt oben ein Gesamtergebnis: »Bereit zum Fräsen«, Warnungen oder Fehler. Jeder Eintrag erklärt, was los ist, und hat meist eine **Lösung** und eine Schaltfläche »Zur Bearbeitung«.

* **Fehler** sperren den Weiter-Knopf zum Fräsen, den G-Code-Export und den Start. Du kannst sie nicht wegklicken. Behebe sie.
* **Warnungen** erlauben das Fräsen. Du kannst eine Warnung bewusst **akzeptieren** (Schaltfläche »Akzeptieren«). Sie zählt dann nicht mehr und erscheint auch bei den Hinweisen nicht. Ändert sich der Sachverhalt, kommt sie zurück. Mit »Wieder zeigen« holst du sie zurück, Strg+Z macht das Akzeptieren rückgängig.
* **Hinweise** informieren nur.

Die Prüfliste meldet unter anderem:

* Tiefe größer als die Materialdicke, Werkzeug zu kurz für die Frästiefe,
* Eilgang durch stehendes Material (siehe unten), Verfahrweg überschritten,
* fehlende Haltestege bei Durchschnitten (nicht bei kleinem Abfall und bei Schlitzen),
* Drehzahl- und Vorschubgrenzen der Maschine, V-Fräser zu tief, leere Werkzeugwege,
* Kollisionen mit Spannmitteln (siehe unten).

**Eilgang in stehendes Material:** Beginnt eine Bearbeitung unter der Oberfläche (Starttiefe über 0) und hat keine frühere Bearbeitung das Material dort entfernt, prallt der Fräser im Eilgang auf. Die Prüfliste simuliert den ganzen Auftrag auf einem groben Höhenraster und meldet das als **Fehler**. Lösung: davor eine Bearbeitung anlegen, die bis zu dieser Tiefe räumt, oder die Starttiefe auf 0 setzen. Die Schwellen sind Annahmen, nicht an echtem Material gemessen. Ein sehr kleiner Fräser (unter etwa 0,4 bis 0,7 mm Durchmesser) kann zwischen den Rasterzellen hindurchfallen und wird dann nicht gemeldet.

## Die 3D-Simulation

Die Simulation spielt den Materialabtrag in 3D ab und rechnet dabei mit den echten Werkzeugwegen.

* **Wiedergabe:** Abspielen und Pause, Neustart, zur vorherigen oder nächsten Bearbeitung springen, zum Ende springen, Geschwindigkeit, Zeitleiste.
* **Ansichten:** Oben, Iso, Seite.
* **Qualität:** »Schnell«, »Ausgewogen« oder »Fein« (mehr Zellen, mehr Rechenzeit).
* **Anzeigen:** Werkzeugbahnen und **Eilgangtreffer**. Zusätzlich zählt die Simulation **Überschnitt** und **Werkzeugwechsel**.
* **Werkzeuge:** Flach-, Kugel- und V-Fräser sowie Bohrer. V-Rillen und die Passung von Inlays werden in Tests gegen die Theorie nachgemessen. Ein Gewindefräser wird als Zylinder ohne Gewindeflanken simuliert.
* **Zeit:** Unter »Auftrag« steht die **geschätzte Laufzeit** (mit Beschleunigung, Eilgang und größtem Vorschub aus dem Maschinenprofil, ohne Werkzeugwechsel). Die Zeit der Wiedergabe rechnet **ohne Beschleunigung** und weicht deshalb ab. Beide sind Näherungen, **nicht mit echten Laufzeiten verglichen**.

Was die Simulation **nicht** kann:

* Sie rechnet mit einem Höhenraster auf dem Prozessor, nicht mit einem vollständigen Festkörper-Modell.
* Sie kennt keine Durchbiegung des Fräsers, keine Späne, keinen Verschleiß und keine Elastizität der Maschine.
* Ein Soll-Ist-Vergleich gibt es nur für 3D-Reliefs, nicht für 2D-Bearbeitungen.
* Fehlt in deinem Grafiktreiber WebGL, bleibt die 3D-Ansicht aus. Prüfliste und Auftragsübersicht funktionieren weiter. Meist hilft ein Treiber-Update.

## Hinweise (Glühbirne)

Eine Regelmaschine analysiert dein Projekt laufend (kurz nach der letzten Änderung) und macht Vorschläge. Sie sperrt nie etwas. Jeder Hinweis hat eine Stufe (»Wichtig«, »Besser so«, »Tipps«), eine Kategorie (Sicherheit, Qualität, Zeit, Ablauf), eine Begründung (**»Warum?«**) und oft eine **Ein-Klick-Behebung**, die als ein einziger Rückgängig-Schritt ausgeführt wird.

Beispiele: Durchschnitt ohne Haltestege, Zustellung zu tief, Vorschub weit über dem Richtwert, Fräser größer als feine Details, Reihenfolge nicht werkzeugsparend, tiefe Tasche besser adaptiv räumen, Sicherheitshöhe zu niedrig, Absaugung nicht eingerichtet, »Erst in der Luft probefräsen«, Gleichlauf bei Holz empfohlen (siehe [Bearbeitungen](Bearbeitungen)).

Hinweise lassen sich ausblenden: für die Sitzung, für dieses Projekt (wird im Projekt gespeichert) oder als ganze Art. Ausgeblendet heißt zugleich »akzeptiert« in der Prüfliste. Fehler lassen sich nie ausblenden.

## Geometrie-Prüfung

Schon beim Zeichnen und Importieren findet die Geometrie-Prüfung: offene oder fast geschlossene Konturen, doppelte Konturen, Selbstschnitte, Mikrosegmente, Innenradien kleiner als der Fräserradius, zu kleine Teile, dünne Stege und Formen außerhalb der Platte. Ein Panel und Markierungen im Zeichenbereich zeigen die Stellen, viele lassen sich mit einem Klick reparieren (ein Rückgängig-Schritt). Mehr dazu unter [Zeichnen und Importieren](Zeichnen-und-Importieren).

## Spannmittel und Sperrzonen

Du kannst Pratzen, Schrauben, Vakuumsauger und Sperrzonen (Bereiche, in die nicht geschnitten werden soll) im Projekt eintragen (Knopf in der Kopfzeile der Bearbeitungsliste). Die Prüfliste prüft dann alle Bewegungen, auch die Fahrten zwischen Bearbeitungen und die Rückfahrt zum Nullpunkt, gegen Fräser, Schaft, Spannmutter und Spindel. Eine Kollision ist ein **Fehler** und sperrt Export und Start. Grenzen: Die Maße von Spannmutter (Ø 22 mm) und Spindel (Ø 65 mm) sind **Annahmen** für eine typische Frässpindel, miss deine nach. Spannmittel gelten als senkrechte Säulen (keine Hinterschneidungen, keine schrägen Pratzenarme). Die erste Anfahrt aus der unbekannten Maschinenposition wird nicht geprüft.

## Sinnvoller Ablauf

1. Prüfliste lesen, Fehler beheben, Warnungen verstehen (und nur bewusst akzeptieren).
2. Simulation einmal ganz abspielen und die Kanten ansehen.
3. In der Zeitleiste kritische Stellen anspringen: Eintauchen, Ecken, Haltestege.
4. Erst dann zum Schritt »Fräsen« wechseln.

## Weiter

* [Fräsen an der Maschine](Fräsen-an-der-Maschine)
* [Bearbeitungen](Bearbeitungen)
* Etwas wird nicht richtig angezeigt? [Fehlersuche](Fehlersuche)
