# Web-Designer im Portal (Küche und Möbel im Browser)

Seit Version 0.5.0 laufen der **Küchen-Designer** und der **Möbel-Designer** auch im [Community-Portal](Community-Portal): im Browser, ohne das Programm zu installieren. Du entwirfst, siehst das Ergebnis in 3D, bekommst Stückliste und Zuschnitt, speicherst den Entwurf in deinem Konto und lädst ihn als Datei herunter, um ihn im Programm weiterzubearbeiten und zu fräsen.

> **Ehrlich zum Stand:** Der Web-Designer ist neu und **nur gegen Tests und in Chromium geprüft**: nicht von mehreren Menschen gleichzeitig, nicht auf dem Server des Betreibers unter Last, nicht in Firefox, Safari oder Handy-Browsern, nicht mit einem echten Mailserver. **Nichts aus den Designern wurde gefräst oder gebaut** (siehe [Möbel-Designer](Moebel-Designer) und [Platten und Möbel](Platten-und-Möbel)). Ein Entwurf ist Planung, kein Nachweis.

## Öffnen

1. Im Portal anmelden. Du brauchst ein Konto mit **bestätigter E-Mail-Adresse** (der Server rechnet nur für bestätigte Konten; die Mail mit dem Bestätigungslink kommt bei der Registrierung, unter *Konto* lässt sie sich erneut anfordern).
2. Auf **»Küche & Möbel entwerfen«** klicken: in der Navigation, im Konto-Menü oder auf der Startseite. Der Designer liegt unter der Adresse `/designer/` des Portals. Ohne Anmeldung führt er zur Anmeldung und danach zurück.
3. Oben zwischen **Küche** und **Möbel** wählen. Die Bedienung ist dieselbe wie im Programm: links die Liste, in der Mitte 3D-Vorschau und Grundriss, rechts die Felder des gewählten Teils; Rückgängig (Strg+Z) und Wiederholen (Strg+Y), Deutsch und English, hell und dunkel.

Was im Programm steht, gilt hier auch: [Möbel-Designer](Moebel-Designer), [Küchen-Rendering](Kuechen-Rendering) und [Platten und Möbel](Platten-und-Möbel).

## Speichern, Öffnen, Herunterladen

* **Speichern** (Strg+S) legt den Entwurf **privat in deinem Konto** ab. Beim ersten Mal fragt der Designer nach einem Namen (Vorschlag mit Datum), danach speichert Strg+S ohne Rückfrage; *Als neuen Entwurf speichern …* legt eine Kopie an. Die Kopfleiste zeigt **Neu**, **Gespeichert** oder **Ungespeichert**; beim Schließen des Tabs warnt der Browser vor ungespeicherten Änderungen.
* **Öffnen** (Strg+O) zeigt deine Entwürfe mit Art (Küche, Möbel, beides), Größe und Datum. Dort kannst du sie auch **umbenennen, herunterladen und löschen**.
* **Grenzen:** höchstens **30 Entwürfe**, zusammen **40 MB**, je Entwurf **8 MB** (der Betreiber des Portals kann das ändern). Die Anzeige zeigt, wie viel belegt ist.
* **Herunterladen (.ocam)** gibt die Projektdatei, die auch das Programm öffnet. Im Programm findest du dann *Teile erzeugen & fräsen vorbereiten*, die Maschine und alles Weitere. Umgekehrt kannst du eine `.ocam` aus dem Programm im Web-Designer öffnen (**Datei öffnen**, bis 8 MB).
* **Zwischenstand:** Dein Browser legt alle 20 Sekunden einen Zwischenstand ab, solange es ungespeicherte Änderungen gibt. Läuft die Sitzung auf dem Server ab, bietet der Designer an, ihn wiederherzustellen. **Das ersetzt das Speichern nicht**; speichere regelmäßig.

## Was es im Web nicht gibt

Fräsen, die Maschine, G-Code, die Einstellungen des Programms, Dateizugriff, eigene Bausteine und eigene Beschläge (die mitgelieferten kannst du wählen), *Teile erzeugen & fräsen vorbereiten*, Claude/MCP und die Kamera. Stückliste (als CSV oder HTML), Zuschnitt, Rendering, Prüfliste, Varianten, Kundenblatt, Muster und Reliefs gibt es. Wo ein Knopf fehlt, steht der Hinweis, den Entwurf herunterzuladen und im Programm weiterzubearbeiten.

## Gut zu wissen

* **Der Server rechnet.** Die Rechnung läuft nicht in deinem Browser, sondern auf dem Server des Portals, in einer abgeschotteten Umgebung je Nutzer (ohne Zugriff auf Dateien, Seriell, Netz). Ohne Verbindung zum Portal geht nichts.
* **Sitzung:** Der Server hält deine Rechnung höchstens **60 Minuten ohne Aufruf**; nach einem Neustart des Servers (Update) ist sie weg. Dann gilt der zuletzt gespeicherte Entwurf (oder der Zwischenstand deines Browsers).
* **Ein Entwurf zur Zeit:** Alle Tabs und Geräte deines Kontos teilen sich dieselbe Rechnung. Arbeite nicht in zwei Tabs gleichzeitig.
* **Zu viel los:** Rechnet der Server schon für viele andere, kommt »Der Server ist gerade ausgelastet«. Einen Moment warten und es noch einmal versuchen.
* **Datenschutz:** Deine Entwürfe liegen in der Datenbank des Portals, nur für dein Konto sichtbar. Der Designer setzt ein Cookie, das deinen Browser mit deiner Sitzung verbindet. Was das Portal sonst speichert, steht in seiner Datenschutzerklärung.

## Für Betreiber eines eigenen Portals

Der Web-Designer braucht das **Server-Image 0.5.0** (das Programm allein reicht nicht). Voreinstellungen und Schalter (`ORTINO_HUB_DESIGNER_*`: gleichzeitige Rechnungen, Zeitgrenzen, Größen, Entwürfe je Konto; abschalten mit `ORTINO_HUB_DESIGNER=off`) stehen in der Betriebsanleitung des Portals im Quelltext-Repository. **Auf einem NAS mit 2–4 Kernen** die Zahl der gleichzeitigen Rechnungen auf die Zahl der Kerne senken; die Last ist nicht gemessen. Gerechnet wird **nur für Konten mit bestätigter E-Mail-Adresse**: Ohne eingerichteten Mailversand (SMTP) kann niemand den Web-Designer benutzen.

## Fehlersuche

| Symptom | Lösung |
|---|---|
| »Bitte bestätige zuerst deine E-Mail-Adresse« | Den Link in der Bestätigungsmail anklicken oder unter *Konto* eine neue Mail anfordern, danach den Designer neu laden. |
| »Die Sitzung ist abgelaufen« | Den letzten gespeicherten Entwurf öffnen oder den Zwischenstand wiederherstellen. |
| »Der Server ist gerade ausgelastet« | Einen Moment warten, dann noch einmal. |
| »Diese Funktion gibt es im Web-Designer nicht« | Den Entwurf herunterladen (.ocam) und im Programm weiterbearbeiten. |
| »Der Platz für Entwürfe in deinem Konto ist voll« | Unter *Öffnen* alte Entwürfe herunterladen und löschen. |
| Es gibt keinen Einstieg im Portal | Der Betreiber hat den Web-Designer nicht eingeschaltet oder das Portal ist noch nicht auf Version 0.5.0. |
