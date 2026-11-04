# Glossar

Kurze Erklärungen der Begriffe, die in ortino.CAM und in diesem Wiki vorkommen. Alphabetisch sortiert.

## A bis F

**Abwärtsspirale, Aufwärtsspirale, Kompressionsfräser:** Bauarten von Fräsern mit Spiralnuten. Sie unterscheiden sich darin, wohin die Späne gefördert werden. Zum Durchschneiden von Sperrholz, beschichteten Platten und Hartholz nennt die Auswahlhilfe der [Fräserbibliothek](Werkzeuge-und-Schnittdaten) zuerst einen Kompressionsfräser, danach Abwärts- oder Aufwärtsspirale. Zu jeder Empfehlung steht die Begründung.

**Adaptives Räumen:** Eine Räumstrategie, bei der das Programm die Belastung des Fräsers gleichmäßig hält, damit tiefe Zustellungen mit der vollen Schneide möglich sind. Siehe [Bearbeitungen](Bearbeitungen).

**Alarm:** Zustand der Steuerung nach einem schwerwiegenden Problem (zum Beispiel Soft-Limit überschritten). Die Steuerung ist gesperrt, bis du sie entsperrst (`$X`) oder eine Referenzfahrt machst. Nach einem Alarm kann die Position verloren sein.

**Antasten:** Der Fräser fährt langsam auf eine Tastplatte oder einen Eckblock, bis ein Kontakt meldet, dass er aufgesetzt hat. Daraus setzt das Programm den Nullpunkt. Siehe [Fräsen an der Maschine](Fräsen-an-der-Maschine).

**Array:** Mehrere Kopien einer Form, im Raster, auf einem Kreis oder entlang eines Pfads angeordnet.

**Bahnabstand (Stepover):** Seitlicher Abstand zweier benachbarter Fräsbahnen, meist in Prozent des Fräserdurchmessers.

**Baudrate:** Übertragungsgeschwindigkeit der seriellen Verbindung zur Steuerung. GRBL-Standard und xPRO V5: 115200.

**Bearbeitung:** Eine Anweisung an das Programm, was mit Formen passieren soll (Profil, Tasche, Bohren …). Aus ihr entsteht der Werkzeugweg.

**Boolesche Operation:** Formen kombinieren: Verschweißen (vereinigen), Subtrahieren, Schnittmenge, Ausschluss.

**Creator** (seit 0.13.0): Ein Generator, der aus wenigen Eingaben ein Werkstück aus Plattenmaterial erzeugt (Teile mit Nuten, Teileliste, Montagehinweise). Siehe [Creator](Creator).

**Dogbone (Hundeknochen):** Eine kleine kreisförmige Freistellung in einer Innenecke, damit ein eckiges Gegenstück hineinpasst, obwohl der runde Fräser die Ecke rundet.

**Drehzahl:** Umdrehungen der Spindel pro Minute (U/min). Sie hängt von Fräser und Material ab.

**Ebene für Ebene, Teil für Teil:** siehe Zustellreihenfolge.

**Eckblock (XYZ-Eckblock):** Ein L-förmiger Block, mit dem du X, Y und Z in einem Zug antasten kannst.

**Eilgang (Rapid):** Schnelle Fahrt ohne Schneiden, zum Beispiel zwischen zwei Bahnen.

**Einfach-Modus:** Darstellungsmodus mit den wichtigsten Einstellungen und Begründungen. Der Experten-Modus zeigt alles.

**Einstich (Eintauchen):** Wie der Fräser ins Material fährt: senkrecht, auf einer Rampe oder auf einer Schraubenbahn (Helix).

**Endschalter:** Schalter an den Achsenenden, mit denen die Steuerung bei der Referenzfahrt ihre Position kennenlernt.

**Fingerzinken:** Eine Eckverbindung mit ineinandergreifenden Zinken. Siehe [Platten und Möbel](Platten-und-Möbel).

**FluidNC:** Eine freie Firmware für Steuerungen mit ESP32. Sie spricht ein GRBL-kompatibles Protokoll.

## G bis O

**G-Code:** Die Textsprache, in der eine Steuerung Fahrbefehle bekommt (`G0` Eilgang, `G1` Linie, `G2` und `G3` Kreisbogen, `M3` Spindel an, `M5` Spindel aus). ortino.CAM erzeugt ihn mit dem passenden [Postprozessor](Postprozessoren-und-Steuerungen).

**Gegenlauf, Gleichlauf:** Die beiden Drehrichtungen des Fräsers relativ zur Vorschubrichtung. Bei **Gleichlauf** beginnt der Span dick und endet dünn, die Kante wird meist sauberer, der Fräser wird ins Material gezogen. Bei **Gegenlauf** beginnt er dünn und endet dick. Die Voreinstellung in ortino.CAM heißt Gegenlauf. Siehe [Bearbeitungen](Bearbeitungen).

**GRBL:** Eine weit verbreitete freie Firmware für Fräsensteuerungen. ortino.CAM spricht GRBL 1.1 und kompatible Steuerungen direkt an. **grblHAL** ist eine Weiterentwicklung für leistungsfähigere Steuerplatinen.

**Gravierstichel:** Ein sehr spitzer Fräser für feine Linien.

**Guillotine-Schnitt:** Ein Schnitt, der durch die ganze Restfläche einer Platte geht, wie an einer Plattensäge. Siehe [Plattenzuschnitt](Plattenzuschnitt).

**Haltesteg (Tab):** Ein stehen gelassener Steg, der ein ausgeschnittenes Teil am Rest der Platte hält, bis du ihn von Hand trennst.

**Handsteuerung (Jog):** Die Maschine mit Tasten oder der Maus in kleinen Schritten von Hand verfahren.

**Helix:** Eine Schraubenbahn. Damit tauchst du ein, bohrst Löcher größer als der Fräser oder fräst ein Gewinde.

**Höhenkarte:** Eine Messung der Höhe der Opferplatte an einem Raster von Punkten. Beim Fräsen folgt die Fräserspitze der Platte. Siehe [Fester Taster und Opferplatte](Fester-Taster-und-Opferplatte).

**Inlay:** Zwei zusammenpassende Teile: eine Aussparung in einer Platte (Weibchen) und ein gespiegelter Einleger (Männchen), der hineinpasst.

**Insel:** Ein Stück Material, das nach dem Ausfräsen ringsum frei geschnitten wäre, zum Beispiel die Mitte eines O. Bei einer Schablone halten **Stege** es am Umfeld. Siehe [Zeichnen und Importieren](Zeichnen-und-Importieren).

**Kantenband:** Ein Streifen, der die Schmalseite einer Möbelplatte verdeckt. Er verändert das Zuschnittmaß.

**Kernloch:** Das vorgebohrte Loch, in dem ein Innengewinde gefräst wird.

**KI-Modell** (seit 0.13.0): Eine Datei mit dem Tiefenmodell für »Foto → Relief«, die auf deinem Rechner rechnet und im Dialog »KI-Modelle« geladen, geprüft oder entfernt wird. Siehe [KI-Modelle und Startseite](KI-Modelle-und-Startseite).

**Komponente (Relief):** Eine Ebene eines Reliefs aus einem Profil, einem Muster oder einem Bild, die mit den anderen addiert, abgezogen oder gemischt wird. Siehe [Reliefs modellieren](Modellieren-von-Reliefs).

**Kugelfräser:** Ein Fräser mit halbkugelförmiger Spitze, zum Beispiel für 3D-Reliefs.

**Kundenstamm:** Die Liste deiner Kunden mit Nummer und Anschrift, aus der das Angebot den Adressblock nimmt. Liegt nur auf deinem Rechner. Siehe [Kunden und Angebote](Kunden-und-Angebote).

**Los:** Im Angebot ein Satz aller Teile des Projekts, alle Platten einmal gefräst. Die Menge ist die Zahl der Lose.

**Luftschnitt:** Das ganze Programm läuft angehoben und ohne Spindel. Ein Testlauf ohne Materialkontakt.

**Maserung:** Faserrichtung des Holzes. Sie wirkt im Zuschnitt und im Plattenplaner.

**Maschinenkoordinaten und Arbeitskoordinaten:** Maschinenkoordinaten beziehen sich auf die Endschalter der Maschine. Arbeitskoordinaten (G54) beziehen sich auf deinen Nullpunkt am Werkstück.

**MCP (Model Context Protocol):** Ein Standard, mit dem KI-Programme wie Claude Werkzeuge anderer Programme benutzen. Siehe [Claude, MCP und API](Claude-MCP-und-API).

**Nesting (Schachteln):** Teile platzsparend auf Platten anordnen.

**Not-Aus:** Der Hardware-Schalter, der die Maschine sofort stromlos macht. Die Schaltflächen im Programm ersetzen ihn nicht.

**Nullpunkt (Werkstücknullpunkt):** Der Punkt, von dem aus alle Koordinaten des Programms zählen. In X und Y meist eine Ecke des Werkstücks, in Z die Oberfläche (oder der Tisch).

**Opferplatte:** Die Platte auf dem Maschinentisch, in die der Fräser beim Durchschneiden eintauchen darf. Sie schützt den Tisch.

## P bis Z

**Parallaxe:** Scheinbare Verschiebung eines Gegenstands, wenn die Kamera ihn aus einem anderen Winkel sieht als seine Umgebung. Bei der [Kamera](Kamera-auf-der-Arbeitsplatte) verschiebt die Dicke des Materials das Bild nach außen.

**Parametrische Skizze:** Eine Zeichnung aus Punkten, Strecken, Kreisen und Bögen, deren Form durch Abhängigkeiten und Maße (auch Formeln) festgelegt ist. Siehe [Zeichnen und Importieren](Zeichnen-und-Importieren).

**Platte:** In ortino.CAM das Material, aus dem du fräst (Größe, Dicke, Material, Nullpunkt).

**Postprozessor:** Das Profil, das Werkzeugwege in den G-Code-Dialekt einer Steuerung übersetzt.

**Profil:** Eine Bearbeitung, die einer Kontur folgt: außen (Teil ausschneiden), innen (Loch ausschneiden) oder auf der Linie (Gravur).

**Prüfliste:** Die Liste der Fehler, Warnungen und Hinweise zu den berechneten Werkzeugwegen. Fehler sperren Export und Maschinenstart.

**Referenzfahrt (Homing):** Die Maschine fährt zu den Endschaltern und kennt danach ihre Position.

**Restschicht (Onion Skin):** Eine dünne Schicht, die beim Ausschneiden am Boden stehen bleibt und zuletzt getrennt wird.

**Rhai:** Die eingebaute Skriptsprache für eigene Werkzeuge.

**Sägeplan:** Der Plan, wie rechteckige Teile mit durchgehenden Schnitten aus Platten gesägt werden. Siehe [Plattenzuschnitt](Plattenzuschnitt).

**Schablonen-Steg:** Eine schmale Brücke aus Material, die eine Insel in einem Schablonenbuchstaben am Umfeld hält. Siehe [Zeichnen und Importieren](Zeichnen-und-Importieren).

**Seriennummer:** Ein Zähler im Text, zum Beispiel `{n:001}`. Er zählt in Arrays und Serien hoch (001, 002, 003 …).

**Sicherheitshöhe:** Die Höhe über dem Werkstück, in der der Fräser für Eilgänge fährt.

**Soft-Limits:** Eine Einstellung der Steuerung, die Fahrten über den Verfahrweg hinaus verhindert. Sie braucht eine Referenzfahrt.

**Spannmittel:** Pratzen, Schrauben, Vakuumsauger, mit denen das Werkstück festgehalten wird.

**Spiel:** Der Luftspalt zwischen zwei ineinandergreifenden Teilen, zum Beispiel bei Fingerzinken (Richtwert 0,1 mm). Den passenden Wert für dein Material liefert der Testcoupon des Passungs-Assistenten. Siehe [Platten und Möbel](Platten-und-Möbel).

**Spindel:** Der Motor, der den Fräser dreht.

**Staffel (Staffelpreise):** Eine Tabelle im Angebot, die den Preis je Los für mehrere Mengen zeigt, zum Beispiel 1, 5, 10 und 25. Das Rüsten fällt nur einmal an, deshalb sinkt der Preis je Los.

**Start-Check:** Prüft vor jedem Lauf den Zustand der Steuerung gegen dein Projekt. Fehler sperren den Start.

**Startseite** (seit 0.13.0): Die Willkommensansicht mit den Schnellzugriffen; die Home-Schaltfläche in der Kopfleiste (`Alt+Pos1`) führt immer dorthin zurück. Siehe [KI-Modelle und Startseite](KI-Modelle-und-Startseite).

**STL, 3MF:** Dateiformate für 3D-Körper. ortino.CAM liest STL (und STEP) ein und schreibt STL und 3MF. Siehe [3D-Körper exportieren](Export-STL-3MF).

**Tasche:** Eine Bearbeitung, die eine Fläche bis zu einer Tiefe ausräumt.

**Tastplatte:** Eine flache Metallplatte bekannter Dicke zum Antasten von Z.

**V-Carving:** Eine Bearbeitung mit einem V-förmigen Fräser, bei der die Frästiefe der Breite der Form folgt.

**Verfahrweg:** Der Weg, den eine Achse höchstens fahren kann.

**Vorschub:** Die Geschwindigkeit, mit der der Fräser durchs Material fährt (mm/min).

**Werkzeugweg:** Die berechnete Bahn des Fräsers.

**Zustellreihenfolge** (seit 0.13.0): Ob bei mehreren Teilen jedes Teil bis zur Endtiefe gefräst wird, bevor das nächste folgt (**Teil für Teil**), oder erst alle Teile um eine Stufe tiefer gehen (**Ebene für Ebene**). Siehe [Bearbeitungen](Bearbeitungen).

**Zustellung:** Wie tief der Fräser pro Durchgang schneidet.

**Z-Null:** Die Höhe, die als Null für Z gilt: entweder die Oberseite der Platte oder der Tisch (die Opferplatte). Siehe [Fräsen an der Maschine](Fräsen-an-der-Maschine).

**`.ocam`, `.ocamd`:** Dateiendungen. `.ocam` ist ein Projekt, `.ocamd` ein Designpaket für das [Community-Portal](Community-Portal).
