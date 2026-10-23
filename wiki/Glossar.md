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

**Dogbone (Hundeknochen):** Eine kleine kreisförmige Freistellung in einer Innenecke, damit ein eckiges Gegenstück hineinpasst, obwohl der runde Fräser die Ecke rundet.

**Drehzahl:** Umdrehungen der Spindel pro Minute (U/min). Sie hängt von Fräser und Material ab.

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

**Haltesteg (Tab):** Ein stehen gelassener Steg, der ein ausgeschnittenes Teil am Rest der Platte hält, bis du ihn von Hand trennst.

**Handsteuerung (Jog):** Die Maschine mit Tasten oder der Maus in kleinen Schritten von Hand verfahren.

**Helix:** Eine Schraubenbahn. Damit tauchst du ein, bohrst Löcher größer als der Fräser oder fräst ein Gewinde.

**Höhenkarte:** Eine Messung der Höhe der Opferplatte an einem Raster von Punkten. Beim Fräsen folgt die Fräserspitze der Platte. Siehe [Fester Taster und Opferplatte](Fester-Taster-und-Opferplatte).

**Inlay:** Zwei zusammenpassende Teile: eine Aussparung in einer Platte (Weibchen) und ein gespiegelter Einleger (Männchen), der hineinpasst.

**Kantenband:** Ein Streifen, der die Schmalseite einer Möbelplatte verdeckt. Er verändert das Zuschnittmaß.

**Kernloch:** Das vorgebohrte Loch, in dem ein Innengewinde gefräst wird.

**Kugelfräser:** Ein Fräser mit halbkugelförmiger Spitze, zum Beispiel für 3D-Reliefs.

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

**Platte:** In ortino.CAM das Material, aus dem du fräst (Größe, Dicke, Material, Nullpunkt).

**Postprozessor:** Das Profil, das Werkzeugwege in den G-Code-Dialekt einer Steuerung übersetzt.

**Profil:** Eine Bearbeitung, die einer Kontur folgt: außen (Teil ausschneiden), innen (Loch ausschneiden) oder auf der Linie (Gravur).

**Prüfliste:** Die Liste der Fehler, Warnungen und Hinweise zu den berechneten Werkzeugwegen. Fehler sperren Export und Maschinenstart.

**Referenzfahrt (Homing):** Die Maschine fährt zu den Endschaltern und kennt danach ihre Position.

**Restschicht (Onion Skin):** Eine dünne Schicht, die beim Ausschneiden am Boden stehen bleibt und zuletzt getrennt wird.

**Rhai:** Die eingebaute Skriptsprache für eigene Werkzeuge.

**Seriennummer:** Ein Zähler im Text, zum Beispiel `{n:001}`. Er zählt in Arrays und Serien hoch (001, 002, 003 …).

**Sicherheitshöhe:** Die Höhe über dem Werkstück, in der der Fräser für Eilgänge fährt.

**Soft-Limits:** Eine Einstellung der Steuerung, die Fahrten über den Verfahrweg hinaus verhindert. Sie braucht eine Referenzfahrt.

**Spannmittel:** Pratzen, Schrauben, Vakuumsauger, mit denen das Werkstück festgehalten wird.

**Spindel:** Der Motor, der den Fräser dreht.

**Staffel (Staffelpreise):** Eine Tabelle im Angebot, die den Preis je Los für mehrere Mengen zeigt, zum Beispiel 1, 5, 10 und 25. Das Rüsten fällt nur einmal an, deshalb sinkt der Preis je Los.

**Start-Check:** Prüft vor jedem Lauf den Zustand der Steuerung gegen dein Projekt. Fehler sperren den Start.

**Tasche:** Eine Bearbeitung, die eine Fläche bis zu einer Tiefe ausräumt.

**Tastplatte:** Eine flache Metallplatte bekannter Dicke zum Antasten von Z.

**V-Carving:** Eine Bearbeitung mit einem V-förmigen Fräser, bei der die Frästiefe der Breite der Form folgt.

**Verfahrweg:** Der Weg, den eine Achse höchstens fahren kann.

**Vorschub:** Die Geschwindigkeit, mit der der Fräser durchs Material fährt (mm/min).

**Werkzeugweg:** Die berechnete Bahn des Fräsers.

**Zustellung:** Wie tief der Fräser pro Durchgang schneidet.

**Z-Null:** Die Höhe, die als Null für Z gilt: entweder die Oberseite der Platte oder der Tisch (die Opferplatte). Siehe [Fräsen an der Maschine](Fräsen-an-der-Maschine).

**`.ocam`, `.ocamd`:** Dateiendungen. `.ocam` ist ein Projekt, `.ocamd` ein Designpaket für das [Community-Portal](Community-Portal).
