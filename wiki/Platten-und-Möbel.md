# Platten und Möbel

Diese Seite beschreibt, wie du viele Teile auf Platten verteilst (**Plattenplaner**), Holzverbindungen erzeugst (**Passungen und Fingerzinken**), Schränke und Küchen entwirfst (**Möbel-Designer**) und Projekte als **Vorlagen** und **Serien aus einer Tabelle** fertigst.

![Möbel- und Küchen-Designer: Küchenzeile in 3D und Frontansicht mit Schrankliste](https://raw.githubusercontent.com/KlapSC/ortino-cam/main/docs/bilder/moebel-light.png)

> **Ehrlich zum Stand:** Alles auf dieser Seite ist **rechnerisch, in der Simulation und im Browser-Test geprüft, aber nie an einer Maschine gefräst und nie in echtem Holz erprobt.** Maße von Beschlägen und Verbindungen stammen teils aus Händlerangaben, teils aus Werkstattpraxis und sind zum Teil unbestätigt. Fräse vor der ersten Serie ein Probeteil und vergleiche es mit dem echten Beschlag oder der Bohrschablone des Herstellers.

## Plattenplaner

Der Plattenplaner legt Teile platzsparend auf eine oder mehrere Platten und erstellt einen Verschnitt-Bericht. Du findest ihn im Eigenschaften-Panel unter »Anordnen« (Knopf **Auf Platte anordnen**) und in der Befehlspalette (`Strg+K`: »Plattenplaner öffnen …«). Im Einfach-Modus genügt ein Klick. Passt etwas nicht, öffnet sich stattdessen der Dialog mit der Vorschau, es wird nie still etwas halb gemacht. Der Dialog zeigt dir **exakt den Plan, den »Übernehmen« danach umsetzt**, als ein Rückgängig-Schritt.

* **Was ist ein Teil?** Das Programm fasst zusammen, was zusammengehört: Eine Form innerhalb einer anderen (Bohrung, Tasche, Beschriftung) gehört zu deren Teil, Innenkonturen bleiben also beim Teil. Sich überschneidende Formen bilden ein Teil.
* **Einstellungen:** Stückzahl je Teil (0 bis 1000), Abstand (mindestens der Fräserdurchmesser, automatisch Durchmesser plus 2 mm), Rand (mindestens 10 mm), Drehung (keine, 90° oder beliebig), Maserung beachten.
* **Zwei Verfahren:** **Rechteckig** (Standard) packt Teile über ihr Hüllrechteck. **Freiform** verschachtelt die echten Konturen (Bögen, Löcher) und spart bei runden, schrägen und L-förmigen Teilen deutlich Material. Bei reinen Rechtecken bringt Freiform nichts. Freiform ist gierig und **kein Optimierer**: Es liefert gültige, meist gute, nicht optimale Anordnungen. Höchstens 500 Teile je Plan.
* **Bearbeitungen folgen den Teilen:** Liegen die Formen einer Bearbeitung danach auf mehreren Platten, entsteht je Platte eine Bearbeitung.
* **Verschnitt-Bericht:** je Platte Ausnutzung, Verschnitt, das größte nutzbare Restrechteck, und eine Liste nicht platzierter Teile mit Grund und Lösung.
* **Reststück-Lager:** Reststücke (mit Maßen, Dicke, Material, Maserung, optional Umriss) gehören zum Projekt. Mit »Reststücke zuerst verwenden« füllt der Plan passende Reststücke zuerst. »Größten Rest jeder Platte merken« trägt den größten freien Bereich nach dem Anordnen ein. Eingetragen wird nicht von selbst nach dem Fräsen. Das Reststück-Lager fließt auch **nicht** in die Kosten ein.

Grenzen: Sperrzonen für Spannmittel kennt der Plattenplaner nicht. Teile aus mehr als 300 Konturen werden über ihre konvexe Hülle angeordnet (mit Lücken). Die Fugen sind wegen des Rasters bis zu etwa zwei Zellen breiter als der Mindestabstand. Schau dir vor dem ersten Schnitt die Simulation an.

## Passungs-Assistent: Wie viel Spiel braucht dein Material?

Ob Zinken in *deinem* Sperrholz passen, hängt von der echten Dicke und von deinem Fräser ab. Der **Passungs-Assistent** (Datei-Menü, Befehlspalette oder die Karte »Passung & Verbindungen« im Projekt-Schritt) findet das mit einem **Testcoupon** heraus:

1. **Dicke messen:** Trage die mit dem Messschieber gemessene Dicke ein (Mittelwert).
2. **Testcoupon erzeugen:** Eine kleine Platte mit mehreren Schlitzen, jeder etwas breiter oder schmaler (Standard: 9 Stufen in Schritten von 0,05 mm). Die Spiele stehen graviert über jedem Schlitz. Fräse den Coupon.
3. **Ergebnis übernehmen:** Stecke einen Reststreifen in jeden Schlitz, wähle die passende Stufe und klicke »Wert übernehmen«. Die Projektvariablen `Dicke` und `Spiel` werden gesetzt, und **alle Verbindungen rechnen sich neu**.

»Dicke antasten« liest ein Antastergebnis der Steuerung. Das ist **nur gegen den Simulator geprüft**.

## Verbindungen: Fingerzinken, Zapfen, Nut und Feder

Der **Verbindungs-Generator** (»Verbindung einfügen …«) erzeugt Konturen und Bearbeitungen für:

| Art | Verwendung |
|---|---|
| **Fingerzinken** | Eckverbindung: ungerade, symmetrische Zinkenzahl, beide Teile enden bündig |
| **Zapfen und Schlitz** | T-Verbindung, durchgesteckt oder als Sackloch |
| **Nut und Feder** | T-Verbindung mit einer Nut im einen Teil |

Dicke und Spiel sind Formeln und mit den Variablen vorbelegt. **Hundeknochen** (kleine Freistellungen in Innenecken) sorgen dafür, dass das eckige Gegenstück in die vom runden Fräser gerundete Ecke passt. Du wählst sie in der Kontur, an der Werkzeugbahn oder gar nicht. Die Teile liegen auf eigenen Ebenen mit fertigen Bearbeitungen (innen vor außen). Ändern sich Dicke, Spiel oder Werkzeug, **rechnen sich die Verbindungen im selben Rückgängig-Schritt neu**. Von Hand geänderte Teile überschreibt das Programm nicht.

Nicht gebaut: Schwalbenschwänze, Gehrungen, Federn dünner als das Brett, Verbindungen mit mehr als zwei Teilen. Eine 3D-Vorschau des zusammengesteckten Zustands gibt es nicht, und die Zinken sind nicht an den Möbel-Designer angebunden. Das Rechenmodell kennt Materialquellung, Feuchte und Fräserverschleiß nicht, und das Spiel ist ein einziger Wert für alle Fugen.

## Möbel- und Küchen-Designer

Öffnen: Datei → *Möbel & Küche …*, `Strg+Umschalt+M` oder die Karte im Projekt-Schritt. Der Designer entwirft Schränke und Küchenzeilen mit wenigen Eingaben und leitet daraus alle Teile mit Bohrungen, Nuten und Taschen ab. Er erstellt Stückliste und Zuschnitt und legt am Ende normale Platten, Formen und Bearbeitungen im Projekt an. Ab da gilt der gewohnte Weg: Bearbeitung → Prüfen → Fräsen.

* **Start in drei Schritten:** Material und Platten wählen (Korpus, Fronten, Rückwand, Plattenformat, Kantenband), Schränke hinzufügen oder die Küchenzeile aus der Raumbreite vorschlagen lassen, dann ändern, was nicht passt.
* **Schranktypen:** Unterschrank, Schubladenschrank, Spülenschrank, Hängeschrank, Hochschrank und Eckschränke (L-Form, Blindeckschrank, auch hängend). Nicht umgesetzt: diagonaler Eckschrank, Karussell, Auszugstechnik, Falttür, 90°-Winkelscharnier.
* **Ansichten:** 3D-Vorschau (Türen öffnen `O`, Explosion `E`, Maße `M`, Bohrungen `B`, Farbe je Schrank `C`) und Frontansicht mit Maßketten.
* **Regeln im Hintergrund:** System 32 (Lochreihen Ø 5, Raster 32 mm), Topfscharniere (Ø 35), Dübel, Exzenterverbinder, Konfirmat, genutete oder aufgesetzte Rückwand, Griffmulden und Griffbohrungen. Die Anzahl der Scharniere richtet sich nach Türhöhe und Gewicht.
* **Kantenband:** Standardband, Matrix aller Teile und Kanten, Zuschnittmaß mit Bandstärke und Fräszugabe.
* **Eigene Bausteine:** Einen Schrank oder eine Gruppe speicherst du als Baustein und fügst ihn wieder ein.
* **Stückliste und Zuschnitt:** Stückliste nach Schrank oder Werkstoff, Export als CSV (Excel-tauglich) und druckbares HTML. Der Zuschnitt verteilt die Teile auf Platten (MaxRects oder sägegerecht als Guillotine) mit Maserung, Abstand und Randabstand.
* **»Teile erzeugen & fräsen vorbereiten«** macht aus allem normale Platten und Bearbeitungen.

Was **nicht** auf der CNC passiert, steht als »Arbeiten von Hand« in Stückliste und Prüfliste: Kantenbohrungen, Auszüge, Klappenbeschläge und die Arbeitsplatte. Griffe selbst sind keine Beschläge im Programm.

> **Prüfe die Beschlagmaße.** Belegt aus einer Quelle sind nur wenige Werte: der Topf des Topfscharniers Ø 35 mm mit Tiefe 13 mm, das Bohrmaß des Exzenterverbinders und das System-32-Raster. Alle Maße von Hettich-Scharnieren, Dübeln und Konfirmaten stammen aus Werkstattpraxis, die Scharnierarme (Überdeckung, Kröpfung) sind Annahmen. Eckschränke und Kantenband sind **intern konsistent, aber nicht gegen Herstellerstandards geprüft**. Vor dem Fräsen mit dem Datenblatt vergleichen und ein Probeteil bauen.

## Vorlagen mit Eingabeformular

Ein Projekt kann zur **Vorlage** werden: Wer sie öffnet, sieht ein Formular mit Maßen, Texten, Material und Schaltern. Das Programm rechnet Formen und Bahnen neu und zeigt Vorschau und Prüfliste daneben.

* **Anlegen:** Projekt-Schritt → Karte »Vorlage & Serie« → »Vorlage anlegen« (oder Befehlspalette: »Als Vorlage speichern …«). Eingabearten: Maß, Zahl, Text, Auswahl, Ja/Nein, Material.
* **Öffnen:** Datei → »Neu aus Vorlage …« oder der Streifen »Vorlagen mit Formular« im Dialog »Neues Projekt«. Mitgeliefert sind ein Namensschild, ein Schneidebrett mit Griff, ein Regalboden mit Bohrraster und ein Lochblech-Panel. Ihre Schnittwerte sind Richtwerte.
* **Formular:** Live-Vorschau und Prüfliste, Fehler am Feld mit Lösung, in jedem Maßfeld Formeln möglich. `Strg+Enter` legt das Projekt an.
* Du kannst Vorlagen als Design im [Community-Portal](Community-Portal) teilen.

## Serien aus einer Tabelle (CSV)

Dieselbe Vorlage lässt sich mit einer Tabelle als **Serie** fertigen: je Zeile ein Teil. Der Serien-Assistent (Formular → »Serie aus Tabelle …«) hat drei Schritte:

1. **Daten:** CSV-Datei wählen, aus Excel einfügen oder eine Beispieltabelle laden. Trennzeichen und Dezimalzeichen erkennt das Programm.
2. **Zuordnung:** Jede Spalte gehört zu einer Eingabe der Vorlage, zur Teilenummer, zur Stückzahl oder zum Dateinamen. Die **Zeilenprüfung** zeigt je Zeile »in Ordnung«, Hinweis oder Fehler mit Zeile, Spalte und Lösung.
3. **Ergebnis:** Ausgabeart, Zielordner, Postprozessor, Beschriftung der Teile (Teilenummer als Text oder Gravur). Dann »Serie fertigen«.

Die Ausgabeart ist entweder **je Zeile eine G-Code-Datei** oder **alle Teile auf Platten verteilt** (der Plattenplaner ordnet sie nach Material und Dicke), je Platte eine Datei. Dazu gibt es ein **Protokoll** als CSV und HTML mit dem Ergebnis jeder Zeile. Das offene Projekt bleibt unverändert, vorhandene Dateien werden nie ohne Bestätigung überschrieben, und fehlerhafte Zeilen halten die übrigen nicht auf. Auf der Kommandozeile geht das mit `ortino series` (siehe [Claude, MCP und API](Claude-MCP-und-API)).

Grenzen: höchstens 2000 Zeilen je Lauf, 20 MB je Tabelle. Im Plattenmodus gilt nur die erste Platte der Vorlage, Inlay und 3D-Relief gehen dort nicht, die Beschriftung sitzt unten mittig im Teil. Ordnerwahl und Pfade unter Windows sowie das Fräsen sind **nicht erprobt**.

## Weiter

* [Bearbeitungen](Bearbeitungen)
* [Rüstblatt und Angebot](Rüstblatt-und-Angebot)
