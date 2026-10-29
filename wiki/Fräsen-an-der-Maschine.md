# Fräsen an der Maschine

Im Schritt **Fräsen** verbindest du ortino.CAM mit deiner GRBL-Steuerung, setzt den Nullpunkt, prüfst alles und startest das Programm. Das Programm sendet den G-Code Zeile für Zeile an die Steuerung (Streaming), zeigt die Werkzeugposition live an und lässt dich pausieren und stoppen.

![Schritt „Fräsen“: simulierte Maschine verbunden, G-Code-Ansicht und Start-Check mit Hinweisen](https://raw.githubusercontent.com/KlapSC/ortino-cam/main/docs/bilder/fraesen-light.png)

> **Ehrlich zum Stand:** Im Echtbetrieb bestätigt ist bisher nur das, was der Betreiber mit Version 0.3.3 an einer **Ultimate Bee mit xPRO V5** gefräst hat: **Taschen, V-Carving, Konturen, Referenzfahrt und Werkzeugwechsel mit erneutem Antasten an der Tastplatte**. Nicht einzeln bestätigt sind Rahmen fahren, Luftschnitt, Pause und Start ab Zeile. **Nur gegen den Simulator und Tests geprüft** sind der Längensensor, der Eckblock, die Absaugung, »An Position fahren«, der feste Taster, die Opferplatte mit Höhenkarte und die übrigen Teile der [Handy-Fernbedienung](Handy-Fernbedienung) (Pause, Anzeige; Stopp, Verfahren und Nullpunkte setzen sind laut Betreiber an einer echten Maschine bestätigt). Andere Steuerungen als die xPRO V5 sind nicht erprobt.
>
> **Sicherheit:** CNC-Maschinen sind gefährlich. Teste zuerst **ohne Werkzeug und ohne Material**, halte den **Hardware-Not-Aus** in Reichweite und lass die Maschine nie unbeaufsichtigt laufen. Die Schaltflächen im Programm ersetzen den Not-Aus nicht. Siehe den [Haftungsausschluss](https://github.com/KlapSC/ortino-cam#haftungsausschluss).

## Der Ablauf im Überblick

1. Mit der Maschine **verbinden**.
2. **Referenzfahrt** ausführen.
3. Mit der **Handsteuerung** an die Werkstückecke fahren und den **Nullpunkt** setzen (X, Y, Z).
4. Den **Start-Check** lesen und die Punkte abarbeiten.
5. **Rahmen fahren** und einen **Luftschnitt** machen.
6. Das **Programm starten**, beobachten, bei Bedarf pausieren.

## Üben ohne Maschine: die Demo

In der Karte **Verbindung** gibt es die Art **Demo**: eine simulierte GRBL-Maschine, ohne Hardware und ohne Risiko. Verbinde dich damit, öffne das Beispielprojekt (siehe [Erste Schritte](Erste-Schritte)) und fahre den ganzen Ablauf einmal durch. Die Bilder in dieser Dokumentation zeigen diesen Simulator. Er ersetzt aber keinen Test an der echten Maschine: Bewegungszeiten sind idealisiert, und Eigenheiten echter Hardware (zum Beispiel Prellen der Endschalter oder USB-Aussetzer) bildet er nicht nach.

## 1. Verbinden

| Art | Eingabe | Hinweis |
|---|---|---|
| **USB** | Anschluss aus der Liste (unter Windows `COM3` o. Ä.), Baudrate 115200 | Der USB-Treiber der Steuerung muss installiert sein (bei der xPRO V5 der CP210x, bei anderen oft CH340 oder FTDI). |
| **Netzwerk** | `Adresse:Port`, zum Beispiel `192.168.1.50:23` | Zum Beispiel FluidNC über WLAN. |
| **Demo** | nichts | Simulator zum Ausprobieren. |

Nach dem Verbinden fragt das Programm die Firmware ab und liest die Einstellungen der Steuerung (nur lesend, siehe [Maschine einrichten](Maschine-einrichten)). Antwortet die Steuerung länger nicht, zeigt die Statusleiste »Keine Antwort«.

**Nicht zum Streamen gedacht** sind Steuerungen ohne GRBL-Protokoll (Mach3/4, LinuxCNC, UCCNC, Centroid, ShopBot, MASSO, PlanetCNC). Für sie exportierst du G-Code mit dem passenden [Postprozessor](Postprozessoren-und-Steuerungen).

## 2. Referenzfahrt

Bei der **Referenzfahrt** (englisch *Homing*) fährt die Maschine zu den Endschaltern und kennt danach ihre Position. Ohne Referenzfahrt kann das Programm den Verfahrweg nicht prüfen. Der Start-Check warnt dann. Die Referenzfahrt braucht Endschalter und `$22=1` in der Steuerung. Der Arbeitsbereich muss frei sein, das Programm fragt vorher nach.

**Immer zur Hand:** Oben in der rechten Spalte steht die Leiste **»Steuerung«**. Sie bleibt beim Scrollen stehen und bietet **Referenzfahrt**, **Entsperren**, **Nullpunkt XY** und **Zu X0 Y0** an, nicht nur beim ersten Mal. Daneben steht, ob die Maschine in dieser Verbindung **referenziert** ist; solange nicht, ist die Referenzfahrt hervorgehoben. Gesperrte Knöpfe bleiben sichtbar, der Satz darunter nennt den Grund (zum Beispiel »nicht verbunden«, »Alarm«, »Programm läuft«). Die Referenzfahrt fragt wie immer vorher nach. *Nur Simulator und Chromium.*

**Erst referenzieren, dann den Nullpunkt setzen.** Die Referenzfahrt legt die Maschinenkoordinaten neu fest; ein vorher gesetzter Nullpunkt liegt danach woanders, und der Start-Check verlangt ihn neu. Dasselbe gilt nach einem Alarm, bei dem die Position verloren geht, oder nach einem Neustart der Steuerung: Bis zur nächsten Referenzfahrt (oder bis du ihn neu setzt) gilt der Nullpunkt als nicht gesetzt. *Nur Simulator.*

## 3. Handsteuerung und Nullpunkt

* **Handsteuerung (Jog):** Pfeiltasten bewegen X und Y, Bild↑ und Bild↓ bewegen Z, mit Umschalt ist der Schritt zehnmal so groß. Die Schrittweite stellst du ein. Im Modus »Dauer« fährt die Maschine, solange du die Taste hältst. Während ein Programm läuft, ist die Handsteuerung gesperrt.
* **Nullpunkt XY:** Fahre den Fräser über die gewünschte Ecke und setze dort **X0 Y0**.
* **Nullpunkt Z:** Tipp die Werkstückoberfläche an (siehe unten). Welche Höhe als Z-Null gilt, stellst du im Projekt ein: **Plattenoberseite** (Standard) oder **Tisch (Opferplatte)**. Bei der zweiten Wahl zählen alle Tiefen von der Opferplatte aus. Das brauchst du für den [festen Taster](Fester-Taster-und-Opferplatte).
* **An Position fahren:** Tippe in die Maschinenansicht, dann fährt die Karte nach Rückfrage erst Z auf die sichere Höhe, danach X und Y. Das geht nur nach der Referenzfahrt. *Nur Simulator.*

### Antasten mit Tastplatte

Eine **Tastplatte** ist eine flache Metallplatte bekannter Dicke, die über eine Klemme am Fräser und ein Kabel an den Taster-Eingang der Steuerung angeschlossen ist. Berührt der Fräser sie, meldet die Steuerung Kontakt.

1. Tastplatte auf das Werkstück legen, Klemme an den Fräser.
2. Mit der Handsteuerung mittig über die Platte fahren, **Spindel aus**.
3. In der Karte »Z-Antasten« die **Dicke der Tastplatte** prüfen und **Z antasten** starten. Der Fräser fährt langsam nach unten, setzt Z0 und hebt wieder ab.
4. Tastplatte entfernen.

Steht im Projekt Z-Null auf »Tisch (Opferplatte)«, fragt die Karte, ob die Platte auf dem Werkstück oder auf der Opferplatte liegt, und rechnet die Materialdicke ein. Ist die Dicke unbekannt, bleibt das Antasten gesperrt. Das Programm rät nicht. Genauer ist es, die Tastplatte auf die Opferplatte zu legen: Dann zählt die eingetragene Materialdicke nicht. *Nur Simulator* (Tisch-Null und die Frage nach der Lage der Tastplatte kamen nach Version 0.3.3 und sind an keiner echten Maschine erprobt).

Das Programm merkt sich beim Antasten und Nullen, für welches Projekt, welche Platte und welche Z-Null-Art Z gesetzt wurde. Öffnest du danach ein anderes Projekt oder stellst die Z-Null-Art der Platte um, verlangt der Start-Check ein neues Antasten. Vor **»Z=0«** in der Positionsanzeige fragt das Programm einmal nach, wo die Fräserspitze dafür stehen muss (Plattenoberseite oder Opferplatte). *Nur Simulator.*

### Antasten mit dem XYZ-Eckblock

Ein **Eckblock** ist ein L-förmiger Aluminiumblock, mit dem du X, Y und Z in einem Zug antastest. Du richtest ihn im Dialog **Zubehör** ein (Karte »Maschine«, Knopf »Zubehör«): Art »XYZ-Eckblock« wählen, die **Wandmaße** mit der Schieblehre messen und eintragen (es gibt bewusst keinen Standardwert) und die Standardecke wählen. Mit »Taster-Eingang testen« prüfst du Kabel und Kontakt. Gemessen wird mit der Mantelfläche des Fräsers, also nur mit zylindrischen Fräsern (Schaftfräsern).

> **Nur gegen den Simulator geprüft.** Ob der Block bündig an der Werkstückecke liegt und die Tastflächen stimmen, kannst nur du prüfen: mit der Schieblehre und einer Luftprobe. Erster Versuch ohne Material.

## 4. Der Start-Check

Der **Start-Check** vergleicht den Zustand der Steuerung mit deinem Projekt. Jeder Punkt hat eine Ampel, eine Erklärung, meist einen Lösungsvorschlag und manchmal eine Ein-Klick-Aktion.

* **Fehler sperren den Start.** Sie lassen sich nicht wegklicken, auch nicht über die Schnittstelle.
* **Warnungen** bestätigst du im Start-Dialog einzeln mit »Verstanden«.
* **Hinweise** informieren nur.

| Prüft zum Beispiel | Warum |
|---|---|
| Verbunden, Leerlauf, kein Alarm | Nur dann nimmt die Steuerung Befehle an. |
| Referenzfahrt in dieser Verbindung | Sonst stimmen Maschinenkoordinaten und Verfahrweg-Prüfung nicht. |
| Programm passt in den Verfahrweg (X, Y, Z-Reserve) | Sonst bräche die Steuerung mit einem Alarm ab. Fehler nur, wenn der Verfahrweg aus der Steuerung stammt, sonst Warnung. |
| Nullpunkt in dieser Verbindung gesetzt | Ein Nullpunkt aus dem Speicher der Steuerung kann veraltet sein. |
| Z-Null passt zu Projekt, Platte, Z-Null-Art, Materialdicke und (beim Wechsel-Assistenten) Werkzeug | Ein Z-Null für eine andere Platte, ein anderes Projekt oder auf dem Tisch statt auf der Oberseite läge um die Materialdicke daneben. Das ist ein Fehler, »Z-Null neu setzen« löst ihn. *Nur Simulator.* |
| Prüfliste des Projekts | Fehler der [Prüfliste](Prüfen-und-Simulation) sperren auch den Start. |
| Koordinatensystem, Einheit, Abstandsmodus (G54, mm, absolut) | Das Programm liest den Zustand der Steuerung mit `$G` und bietet »G54 wählen«, »G21 wählen«, »G90 wählen« an. |
| Vorschub-, Eilgang- und Spindel-Override auf 100 % | GRBL behält sie über das Programmende. |
| Werkzeug, Werkzeugwechsel, Absaugung | Siehe unten. |
| Standzeit und Wartung | Siehe [Werkzeuge und Schnittdaten](Werkzeuge-und-Schnittdaten). |

Der Start-Check ist eine Hilfe, **keine Sicherheitsfunktion**. Er läuft laufend in der Karte und noch einmal unmittelbar vor dem Senden. Verhalten echter Firmware ist nur gegen den Simulator geprüft.

## 5. Probelauf: Rahmen und Luftschnitt

* **Rahmen fahren:** Die Maschine fährt mit **ausgeschalteter Spindel** auf sicherer Höhe den Umriss deines Auftrags ab (1500 mm/min). Du siehst, ob das Werkstück darunter passt. Die Form ist **Rechteck** oder **Kontur** (konvexe Hülle der Schneidbewegungen, höchstens 64 Ecken). Gezeigt wird die Bahn der Werkzeugmitte. Der Fräser ragt um seinen Radius darüber hinaus.
* **Luftschnitt:** Das ganze Programm läuft **angehoben** und **ohne Spindel** (im Start-Dialog bei »Lauf« wählen). Der Ablauf ist derselbe wie beim Fräsen, nur ohne Materialkontakt. Ideal für den ersten Test von Nullpunkt, Richtung und Verfahrweg. Ein gestreiftes Band »LUFTSCHNITT läuft« zeigt den Modus an.

## 6. Werkzeugwechsel

Hat dein Projekt mehrere Werkzeuge, stoppt das Programm beim Wechsel. Im Start-Dialog (oder im Zubehör) wählst du den Modus:

| Modus | Ablauf | Stand |
|---|---|---|
| **Automatisch** | Mit eingerichtetem festem Taster wie »Fester Taster«, sonst wie »Pause«. Der Start-Check zeigt, was gilt. | Standard seit 0.3.12; die Auflösung ist nur Simulator und Tests geprüft |
| **Pause (M0)** | Das Programm hält an, du wechselst. Die Fräser müssen gleich lang eingespannt werden. | Ohne festen Taster das Verhalten von »Automatisch« |
| **Tastplatte** | Nach dem Wechsel tastest du Z mit der Tastplatte neu an. Der Assistent führt dich durch: anhalten, wechseln, antasten, weiter. | **Im Echtbetrieb bestätigt** (Ultimate Bee, Version 0.3.3, Z-Null = Plattenoberseite). Mit Z-Null = Tisch (Materialdicke zur Plattendicke), mit einer Wechselposition und die Prüfung im Start-Check, dass Z-Null zum ersten Werkzeug des nächsten Laufs gehört: **nur Simulator**. |
| **Längensensor** | Ein fest montierter Sensor misst die Länge des neuen Werkzeugs. | **Nie an einer echten Maschine erprobt.** Falsche Sensorposition heißt: Der Fräser fährt an die falsche Stelle. Erster Versuch ohne Material mit niedrigem Override. |
| **Fester Taster** | Die Maschine misst jedes Werkzeug und legt Z-Null auf die Opferplatte. | Einrichten und Einmessen laut Betreiber an einer echten Maschine bestätigt (0.3.10); **Wechsel im Programm nur Simulator**, siehe [Fester Taster und Opferplatte](Fester-Taster-und-Opferplatte). |

Während des Wechsels ist die Handsteuerung erlaubt, sonst nichts. Eine **Wechselposition** und eine sichere Höhe stellst du im Zubehör ein. Ein automatischer Werkzeugwechsler (`M6`) wird nicht unterstützt.

## 7. Während des Laufs

* **Pause** hält den Vorschub an. **Die Spindel läuft weiter**, es ist kein Not-Halt. **Fortsetzen** macht weiter.
* **Stopp** hält an und schaltet die Spindel aus. Danach setzt das Programm die Steuerung zurück. Je nach Einstellung musst du neu referenzieren.
* **Overrides** ändern Vorschub, Eilgang und Spindeldrehzahl live. »Auf 100 % zurücksetzen« stellt sie zurück.
* **Fehler und Alarm:** Bei einem Fehler hält der Auftrag an und nennt Zeile und Grund. Ein Alarm leert die Warteschlange, die Steuerung schaltet Spindel und Absaugung ab. Weiterfahren geht dann nicht, nur Abbrechen und »Start ab Zeile«.
* **Benachrichtigungen:** Auf Wunsch melden Ton, blinkende Taskleiste und eine Systemmeldung, wenn der Auftrag fertig ist, ein Fehler auftritt, ein Werkzeugwechsel wartet oder das Programm pausiert. *Unter Windows nicht geprüft.*
* **Verbindungswächter:** Antwortet die Steuerung 8 Sekunden lang nicht, hält das Programm den Vorschub an und meldet einen Zwischenfall. Der Hinweis bleibt auch nach dem Neuverbinden sichtbar.
* **Ruhezustand:** Während eines Auftrags verhindert das Programm den Ruhezustand von Windows. *Nicht unter Windows erprobt.*

> **Tipp bei Verbindungsabbrüchen:** Die häufigste Ursache ist das USB-Energiesparen von Windows. Schalte in den Energieoptionen das »selektive USB-Energiesparen« aus, entferne im Geräte-Manager bei den USB-Hubs und dem COM-Anschluss das Häkchen »Computer kann das Gerät ausschalten …« und halte das USB-Kabel kurz und getrennt von Motor- und Spindelleitungen.

## 8. Start ab Zeile

Nach einer Unterbrechung (Stromausfall, Fräserbruch, Alarm) kannst du ab einer beliebigen Zeile weitermachen: Klicke in der G-Code-Ansicht auf die Zeile. Das Programm rekonstruiert aus den Zeilen davor den Zustand (Einheiten, Werkzeug, **Absaugung**, Spindel mit Drehrichtung, Vorschub, Position), fährt sicher zur Stelle (erst Z hoch, dann XY, dann Eintauchen mit höchstens 600 mm/min) und zeigt dir im Start-Check genau, was es sendet. Zustände, die sich nicht wiederherstellen lassen (zum Beispiel relative Koordinaten oder aktive Bohrzyklen), lehnt es ab. Prüfe vorher Referenzfahrt, Nullpunkt und Werkzeug. *Nie an einer echten Steuerung erprobt.*

## 9. Absaugung

Im Zubehör legst du fest, an welchem Ausgang deine Absaugung hängt (`M8`, `M7`, `M62` oder `M64`), mit Vorlauf (Standard 2 s) und Nachlauf (5 s). Der Ausgang liefert nur ein Steuersignal. Die Absaugung braucht ein passendes Relais oder Schütz, Netzspannung gehört in die Hände einer Fachkraft. Welche Ausgänge deine Firmware kennt, steht in deren Dokumentation. Die Tabelle im Programm stammt daraus, **nicht aus Versuchen**.

## Weiter

* [Fester Taster und Opferplatte](Fester-Taster-und-Opferplatte)
* [Handy-Fernbedienung](Handy-Fernbedienung)
* [Kamera auf der Arbeitsplatte](Kamera-auf-der-Arbeitsplatte)
* Wenn etwas nicht klappt: [Fehlersuche](Fehlersuche)
