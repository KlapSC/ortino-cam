# Handy-Fernbedienung

Du stehst an der Maschine, der Rechner mit ortino.CAM ist nicht in Reichweite? Mit dem Handy siehst du, was die Maschine tut, fährst sie in kleinen Schritten an eine Stelle (zum Beispiel zum Einrichten des Werkstücks), setzt den Nullpunkt in X und Y und hältst sie an.

> **Ehrlich zum Stand:** Laut Rückmeldung des Betreibers sind **Stopp, Verfahren (X, Y und Z, hoch und runter) und das Setzen der Nullpunkte** an einer **echten Maschine** (Ultimate Bee mit xPRO V5, mit einem Handy im WLAN) bestätigt. **Nicht einzeln bestätigt** sind Pause und Weiter, die Anzeige von Position und Fortschritt, mehrere gekoppelte Handys sowie andere Handys und Browser (welches Handy und welcher Browser benutzt wurden, ist nicht festgehalten). Alles Übrige ist gegen den Simulator und automatische Tests geprüft.
>
> **Die Verbindung ist nicht verschlüsselt.** Benutze die Fernbedienung nur in deinem **eigenen, vertrauenswürdigen WLAN**, nur an einer Maschine mit erreichbarem **Not-Aus**, und schalte sie aus, wenn du sie nicht brauchst. Der Stopp-Knopf am Handy ersetzt den Not-Aus nicht und ist nie die einzige Sicherung. Siehe den [Haftungsausschluss](https://github.com/KlapSC/ortino-cam#haftungsausschluss).

## Einrichten in vier Schritten

1. **Einschalten:** Schritt »Fräsen« → Karte **Handy-Fernbedienung** → Schalter an. Beim Programmstart ist sie **immer aus**, und es wird nichts gespeichert. Die Karte gibt es nur im Desktop-Programm.
2. **WLAN prüfen:** Handy und Rechner müssen im **gleichen lokalen Netz** sein. Stimmt die angezeigte Adresse nicht (mehrere Netzwerkkarten, VPN), trage unter »Adresse ändern« die IPv4-Adresse deines Rechners im WLAN ein (nur private Adressen wie `192.168.x.x`).
3. **Koppeln:** Scanne mit der Kamera des Handys den **QR-Code** auf der Karte und öffne den Link. Die Seite koppelt sich selbst. Der Code gilt **einmal** und **fünf Minuten**. Danach zeigt die Karte von selbst einen neuen, oder du klickst auf »Neuer Code«.
4. **Firewall:** Fragt Windows beim ersten Einschalten nach der Firewall, erlaube den Zugriff **nur für private Netzwerke**.

Bis zu **vier Handys** lassen sich koppeln. Die Karte listet sie mit der Verbindungsgüte. »Trennen« macht ein Gerät sofort wertlos, »Alle trennen« beendet alle Kopplungen. Beim Ausschalten und beim Beenden von ortino.CAM sind **alle Kopplungen weg**. Beim nächsten Einschalten koppelst du neu.

## Was das Handy darf

| Darf | Einzelheiten |
|---|---|
| **Ansehen** | Zustand (bereit, fräst, pausiert, Alarm …), Positionen, Vorschub, Drehzahl, Fortschritt des Programms |
| **Verfahren** | X, Y und Z einzeln, in X und Y auch **schräg** (die vier Pfeile in den Ecken des Kreuzes: beide Achsen fahren denselben Schritt, also genau 45°; Z fährt immer allein). Schritte in XY 0,1 / 1 / 10 mm, in Z 0,1 / 1 / 5 mm. Tempo langsam (300), mittel (1000), schnell (2000 mm/min), nie über der Grenze deiner Maschine. **Kein Dauerfahren:** Jeder Tipp ist eine begrenzte Strecke. Nur im Leerlauf. |
| **Fahrt abbrechen** | jederzeit |
| **Nullpunkt X und Y** setzen | nur im Leerlauf, mit Rückfrage auf dem Handy |
| **Pause, Weiter, Stopp** | Der rote Stopp-Knopf ist immer sichtbar. »Weiter« geht nicht, solange ein Werkzeugwechsel am Rechner wartet. |
| **Spindel aus** | nur ausschalten, nie einschalten |

**Ausdrücklich nicht:** Programm starten, Referenzfahrt, Antasten, Alarm lösen, Spindel einschalten, Z-Nullpunkt setzen, an eine Position fahren, freie G-Code-Zeilen, Werkzeugwechsel, Projekt ändern. Das sind bewusste Grenzen. Sie bleiben am Rechner, wo der Start-Check läuft. Der Server nimmt vom Handy nur die oben genannten sieben Arten von Befehlen an und prüft jeden Wert.

## Bremsen und Sperren

* **Streckenbudget:** Pro Handy sind in jedem Fenster von 5 Sekunden höchstens **60 mm** Verfahrstrecke erlaubt (ein Schrägschritt zählt mit seiner Diagonale: 10 mm schräg sind 14,1 mm), mit 250 ms Mindestabstand zwischen zwei Schritten. Ein paar Tipps beim Einrichten bleiben ungebremst. Wer darüber hinaus weitertippt, bekommt »Zu viel Strecke in kurzer Zeit«, und der Befehl geht nicht zur Maschine. Größere Wege fährst du am Rechner.
* **Verbindungsgüte:** Das Handy meldet alle halbe Sekunde einen »Herzschlag«. Ist die Verbindung unruhig, sperrt die Steuerung (Verfahren, Nullpunkt, Weiter) sofort und gibt erst wieder frei, wenn sie **5 Sekunden lang durchgehend gut** war. **Immer erlaubt** bleiben Stopp, Fahrt abbrechen, Pause, Spindel aus und der Status. Die Schwellen sind Annahmen, keine Messungen.
* **Ausfall während einer Fahrt:** Bleibt der Herzschlag länger als 1,5 Sekunden aus, bricht das Programm die laufende Fahrt ab. Ein **laufendes Programm hält dabei nicht an**, wenn das Handy wegfällt.
* **Nur im selben Netz:** Das Programm prüft, dass das Handy im gleichen lokalen Netz liegt (gleiches `/24`-Netz) und die Verbindung stabil ist. Es kann **nicht unterscheiden, ob WLAN oder Kabel**. Liegt dein Handy in einem anderen Adressblock deines Heimnetzes, wird es abgewiesen.

## Was dich schützt, und was nicht

Geschützt: kein offener Port ohne dein Einschalten, ein zufälliger Port, Kopplungscode mit 128 Bit (fünf Minuten, einmal), Zugangsschlüssel mit 256 Bit (nur im Speicher, nach dem Koppeln im Handy), Sperre nach fünf Fehlversuchen, Schutz vor Seitenaufrufen aus fremden Webseiten. Die Verwaltung (Ein- und Ausschalten, Koppeln) ist der Oberfläche vorbehalten. Claude, die lokale Schnittstelle und Skripte erreichen sie nie.

Nicht geschützt, und das musst du wissen:

* **Keine Verschlüsselung.** Wer in deinem WLAN mitlesen kann, sieht Positionen und Befehle und kann den Zugangsschlüssel des Handys abgreifen.
* In einem **Gäste-WLAN** oder Netz ohne Geräte-Trennung liegen fremde Geräte im selben Adressbereich. Benutze die Fernbedienung nur dort, wo alle Geräte vertrauenswürdig sind.
* **Wer das entsperrte Handy hat, kann steuern**, wie bei der Funkfernbedienung einer Maschine. Der Zugangsschlüssel bleibt im Handy gültig, bis es getrennt wird, der Server aus ist oder das Gerät acht Stunden still war.
* Die Kopplung per QR-Code beweist nur, dass jemand den Bildschirm sieht. Wer den Code abfotografiert, kann koppeln. Deshalb gibt es die Meldung »Handy gekoppelt« und die Geräteliste.
* Ein Gerät im selben Netz kann den Fernbedienungs-Server belasten und ihn **zeitweise blockieren**, auch den Stopp am Handy.
* Das Programm kann nicht prüfen, wo die Maschine steht oder wer davor steht.

Die Soft-Limits und Alarme der Steuerung gelten unverändert.

## Wenn es nicht klappt

| Beobachtung | Mögliche Ursache und Lösung |
|---|---|
| Das Handy erreicht die Adresse nicht | Nicht im gleichen WLAN. Windows-Firewall hat das Programm blockiert (App zulassen, nur private Netzwerke). Gästenetz mit Geräteisolation im Router. Falsche Adresse: »Adresse ändern«. |
| Die Seite lädt, aber die Kopplung schlägt fehl | Code abgelaufen oder benutzt: »Neuer Code« und neu scannen. Vier Geräte schon gekoppelt: eines trennen. »Zu viele Fehlversuche«: 60 Sekunden warten. |
| »Nicht mehr gekoppelt« | Getrennt, ausgeschaltet oder acht Stunden still: QR-Code neu scannen. |
| Knöpfe gesperrt, »Verbindung zu unruhig« | Näher an den Router, anderes WLAN-Band. Nach 5 Sekunden guter Verbindung wieder frei. |
| »Zu viel Strecke in kurzer Zeit« | Einige Sekunden warten, größere Wege am Rechner fahren. |
| Knöpfe gesperrt, »Programm läuft« oder »Alarm« | Verfahren geht nur im Leerlauf. Alarm löst du am Rechner. |
| Handy im anderen Adressblock | Handy und Rechner in dasselbe `/24`-Netz legen. |

Ob die Seite im Energiesparmodus des Handys weiterfunkt, ist nicht untersucht. Im Hintergrund funkt sie nicht, dann sperrt die Steuerung.

## Weiter

* [Fräsen an der Maschine](Fräsen-an-der-Maschine)
* Sicherheitslücken in der Fernbedienung melden: bitte **nicht** als öffentliches Issue, sondern wie in der [Sicherheitsrichtlinie](https://github.com/KlapSC/ortino-cam/blob/main/SECURITY.md) beschrieben.
* Einen Test mit echtem Handy und Maschine zu melden hilft uns sehr: [Mitmachen und Tests](Mitmachen-und-Tests).
