# Doppelseitig fräsen

Manche Werkstücke brauchen Bearbeitungen von **beiden Seiten**: eine Tasche oben und eine Fase unten, ein Griff, der von hinten ausgefräst wird, ein Schild mit Gravur auf Vorder- und Rückseite. ortino.CAM hilft dabei mit **zwei Passstiften**: Seite A bohrt zwei Löcher durch das Werkstück bis in die Opferplatte, du steckst Stifte hinein, wendest das Werkstück, steckst es auf die Stifte, und Seite B liegt genau dort, wo sie hingehört.

> **Ehrlich zum Stand:** Doppelseitiges Fräsen ist **nur gegen den Simulator, automatische Tests und im Browser (Chromium) geprüft, nie an einer echten Maschine** und nicht systematisch unter Windows (WebView2) geprüft. Wie genau Seite B auf Seite A passt, hängt von deinen Stiften, dem Bohrer und der Opferplatte ab, und das ist **nicht erprobt**. Probiere es beim ersten Mal an einem Reststück, nimm Stifte mit wenig Spiel und fahre vor Seite B den Rahmen.

## Wie es funktioniert

* **Seite B ist eine eigene Platte** mit derselben Breite, Höhe, Dicke, demselben Material und demselben Nullpunkt wie Seite A. Du zeichnest sie so, **wie sie nach dem Wenden von oben aussieht**.
* Der G-Code beider Seiten ist ganz gewöhnlicher G-Code. **Nichts wird beim Export gespiegelt.** Gespiegelt wird nur in den Hilfen beim Zeichnen.
* Die zwei **Passlöcher** liegen spiegelbildlich zur **Wendeachse**. Nach dem Wenden liegen sie deshalb wieder an denselben Stellen der Platte. Auf Seite A werden sie gebohrt, auf Seite B sind sie nur als Markierung eingezeichnet.

| Wendeachse | So wendest du | Ein Punkt links unten auf Seite A liegt danach |
|---|---|---|
| **Senkrecht** (Vorgabe) | über die senkrechte Mittellinie, links und rechts tauschen, wie beim Umblättern einer Buchseite | rechts unten |
| **Waagerecht** | über die waagerechte Mittellinie, oben und unten tauschen, wie beim Umblättern eines Kalenderblatts | links oben |

## Was du brauchst

* Zwei **Passstifte** (zum Beispiel Holzdübel oder Stahlstifte) im Durchmesser des Bohrers, mit dem die Löcher gebohrt werden. Vorgeschlagen wird ein Werkzeug nahe 6 mm.
* Eine **Opferplatte**, in die die Löcher einige Millimeter tief gehen dürfen (Vorgabe 4 mm). ortino.CAM kennt ihre Dicke nicht. Prüfe selbst, dass sie deutlich dicker ist.
* **Verschnitt am Rand:** Die Löcher brauchen Platz außerhalb deiner Teile, Vorgabe 12 mm vom Rand bis zur Lochmitte.
* Am besten **Z-Null auf dem Tisch** (der Opferplatte). Dann gilt ein Nullpunkt für beide Seiten. Mit Z-Null auf der Oberseite musst du nach dem Wenden neu antasten.

## Schritt für Schritt

1. **Seite A zeichnen** und ihre Bearbeitungen anlegen. Lass Abstand zum Plattenrand.
2. Menü **Erstellen → »Doppelseitig fräsen …«** (oder Befehlspalette `Strg+K`, »doppelseitig«). Der Assistent hat drei Schritte:
   * **Wendeachse:** senkrecht oder waagerecht, mit Skizze.
   * **Passstifte:** Werkzeug, Lage der Löcher (»Auf der Wendeachse« oder »An den Rändern«), Randabstand, Tiefe in die Opferplatte und ein **Versatz gegen falsches Wenden**. Rechts siehst du die Platte mit den Löchern und darunter die Prüfmeldungen, jede mit Lösung. Ein Loch, das zu nah an einem Teil liegt, ist rot.
   * **Am Tisch:** Lagen der Stifte relativ zum XY-Nullpunkt, Bohrtiefe, die Namen der G-Code-Dateien und eine nummerierte Anleitung.
3. **Übernehmen.** Die Platte heißt jetzt »Seite A«, dahinter entsteht »Seite B«. Beide Seiten bekommen die gesperrte Ebene »Passstifte« mit den Markierungen. Seite A bekommt die Bohrung »Passlöcher bohren« als **erste** Bearbeitung. Das ist ein einziger Rückgängig-Schritt.
4. **Seite B zeichnen.** Oben rechts im Zeichenbereich steht eine Leiste mit:
   * **»Gegenseite«:** Die andere Seite scheint gestrichelt durch, schon gespiegelt. So siehst du, wo die Teile von Seite A nach dem Wenden liegen.
   * **»Gespiegelt kopieren«:** Die Auswahl (etwa die Außenkontur) wird gespiegelt auf die andere Seite kopiert. Auch im Kontextmenü unter »Spiegeln«.
   * **»Zu Seite A/B«** und die Einstellungen.
5. **Prüfen.** Die Prüfliste meldet, wenn etwas an der Kopplung nicht stimmt (siehe unten).
6. **Seite A fräsen.** Der Start-Check erinnert daran, dass zuerst die Passlöcher gebohrt werden. Lege keine Spannmittel über die Löcher.
7. **Wenden:** Werkstück lösen, Späne aus den Löchern blasen, die Stifte in die Löcher der Opferplatte stecken, das Werkstück über die Wendeachse wenden, auf die Stifte stecken und spannen. Den XY-Nullpunkt **nicht** verändern.
8. **Seite B fräsen.** Der Start-Check fragt **»Werkstück gewendet und auf die Passstifte gesteckt?«**, das musst du bestätigen. Er sagt auch, ob ein vollständiger Lauf von Seite A im Job-Protokoll steht, und ob Z-Null weiter gilt.

**Ändern:** Der Assistent öffnet sich mit den bisherigen Werten. **Aufheben:** »Erstellen → Doppelseitig aufheben …« entfernt Kopplung, Markierungen und Bohrung, Seite B bleibt als eigene Platte. Löschst du eine der beiden Seiten, ist die Kopplung ebenfalls aufgehoben. Das Programm sagt es vorher, und »Rückgängig« stellt alles wieder her.

## Was zusammenbleibt

* Änderst du an einer Seite Breite, Höhe, Dicke, Material oder Nullpunkt, übernimmt die andere Seite den Wert.
* Die Bohrtiefe ist **Dicke plus Zugabe**. Änderst du die Dicke, folgt die Tiefe.
* Die Löcher und Markierungen werden nach jeder Änderung neu berechnet.
* Der **Plattenplaner** legt keine Teile über die Löcher oder dicht daneben. Er verschiebt aber die Teile einer Seite, ohne die andere Seite mitzunehmen. Prüfe danach mit »Gegenseite«.
* **Vorlagen und Serien:** Eine Serie als einzelne Dateien erzeugt je Zeile die G-Code-Dateien beider Seiten. Im Plattenmodus lässt sich eine doppelseitige Vorlage nicht anordnen, das Programm sagt es mit Lösung.

## Was die Prüfliste meldet

| Meldung | Was zu tun ist |
|---|---|
| Seite A und B unterscheiden sich in Maß, Dicke, Material oder Nullpunkt | eine Seite an die andere angleichen, dann folgen sie wieder einander |
| Z-Null ist »Plattenoberseite« | lieber Z-Null »Tisch (Opferplatte)« wählen, sonst auf Seite B neu antasten |
| Werkzeug fehlt oder passt nicht (V-Fräser, Gewindefräser) | einen Bohrer oder Schaftfräser im Durchmesser der Stifte wählen |
| Ein Loch liegt nicht ganz auf der Platte oder zu nah an einem Teil (Seite A oder B) | Randabstand ändern, die andere Lage wählen oder die Teile weiter vom Rand weg legen |
| Die Bohrung fehlt, ist ausgeschaltet oder nicht die erste Bearbeitung | fehlt sie, legt »Änderungen übernehmen« im Assistenten sie neu an; sonst einschalten oder in der Liste der Bearbeitungen nach oben schieben |
| »Bohrt nicht durch«: Tiefe kleiner als Dicke plus 2 mm | Tiefe in die Opferplatte erhöhen |
| Beide Seiten heißen gleich | eine Seite umbenennen, sonst bekämen die G-Code-Dateien denselben Namen |
| Hinweis zur Opferplatte | Stiftdurchmesser und -länge stehen dabei, die Stifte dürfen nicht über die Oberseite stehen |

## Rüstblatt und G-Code

* Jede Seite bekommt ihre eigene G-Code-Datei, zum Beispiel `Kiste_Seite_A.nc` und `Kiste_Seite_B.nc`.
* Das [Rüstblatt](Rüstblatt-und-Angebot) jeder Seite hat einen Abschnitt »Doppelseitig: Seite A → Wenden → Seite B« mit Wendeachse, Stiften, Stiftlagen, Bohrtiefe und den Schritten am Tisch. Auf Seite B steht ein zusätzliches Kästchen »Seite A ist gefräst, Werkstück gewendet«.

## Grenzen

* Die **Simulation** zeigt jede Seite für sich. Seite B wird aus einem vollen Block simuliert, die schon gefräste Seite A wird nicht berücksichtigt.
* Immer **zwei Stifte**. Wenden an einer Anschlagkante oder eine Passform in der Opferplatte gibt es nicht.
* Ohne **Versatz** passt das Werkstück auch falsch gewendet auf die Stifte (um 180° gedreht). Ein Versatz von einigen Millimetern verhindert das.
* **Gespiegelt kopieren** spiegelt auch Texte (Spiegelschrift). Für Schrift auf Seite B lieber neu schreiben.
* Das Job-Protokoll erkennt Seite A am Projekt- und Plattennamen. Nach dem Umbenennen oder bei einem Lauf an einem anderen Rechner bleibt es bei der Warnung zum Bestätigen.
* Die Prüfliste meldet auf Deutsch; der Assistent zeigt dieselben Meldungen auch auf Englisch.
