# Sicherung im Portal

Mit einem Konto im Community-Portal kannst du **Maschinenprofile**, deine **eigenen Fräser** (»Meine Bibliothek«) und eine feste Auswahl der **Programmeinstellungen** privat sichern und später auf demselben oder einem anderen Rechner wieder abrufen: nach einer Neuinstallation oder um zum Beispiel Büro und Werkstatt abzugleichen. **Nichts davon geschieht von selbst** – gesichert und abgerufen wird nur, was du im Dialog auslöst.

> **Ehrlich zum Stand (ab Version 0.3.12):** Geprüft ist die Sicherung gegen einen **echten Portal-Server** mit Datenbank, mit dem Simulator und im Browser (Chromium) mit zwei Programmen, die Büro und Werkstatt vorspielen. **Noch nicht** gegen das Portal im Internet und **nicht unter Windows** (WebView2, Anmeldeinformationsspeicher). Du brauchst ein Portal ab Version 0.3.12; ein älteres sagt das Programm und bietet die Sicherung nicht an. Alles andere funktioniert wie bisher.

## Aufrufen

Menü **Einstellungen ▸ Sicherung im Portal …**, in der Community die Karte *Sicherung im Portal …* auf der Seite *Konto*, oder die Befehlspalette (`Strg+K`, »Sicherung«). Der Dialog zeigt oben, bei welchem Portal du als wer angemeldet bist. Ist noch kein Portal eingerichtet oder du nicht angemeldet, führt er zur Anmeldung (siehe [Community-Portal](Community-Portal)).

## Sichern

1. Hake an, was gesichert werden soll: *Maschinenprofile* (nur deine **eigenen**, nicht die mitgelieferten Vorlagen), *Meine Fräser*, *Einstellungen*.
2. Klicke **Sichern**. Von jeder angehakten Art entsteht ein neuer Stand im Portal; bis zu **10 Stände je Art** bleiben erhalten, dann verdrängt der neueste den ältesten.
3. Je Art steht danach das Ergebnis da (»gesichert«, »nichts zu sichern« oder ein Fehler mit Lösung). Eine Art, die scheitert, hält die anderen nicht auf.

## Abrufen: erst die Vorschau

**Abrufen** ändert zunächst nichts, sondern zeigt eine **Vorschau**. Du wählst den **Stand** (den neuesten, einen älteren oder eine lokale Kopie vom Ersetzen) und die Art der Übernahme:

| Wahl | Was passiert |
|---|---|
| **Zusammenführen** (Standard) | Nur **Neues** kommt dazu. Was es hier schon gibt, bleibt; Doppeltes wird übersprungen; ein vorhandenes, aber abweichendes Profil wird **nie** still überschrieben. |
| **Ersetzen** | Der Stand hier wird gleich dem Stand im Portal. Das Programm fragt ausdrücklich nach, nennt, was entfernt und ersetzt wird, und legt **vorher** automatisch eine **lokale Kopie** an, aus der du zurückkehren kannst. |

Die Vorschau führt jeden Eintrag einzeln auf: **neu**, **gleich vorhanden**, **vorhanden, aber abweichend**, **ungültig** (wird nie übernommen, mit Grund). Bei den *Einstellungen* siehst du eine **Liste der Unterschiede** in Klartext (Wert hier, Wert im Portal); jede Einstellung lässt sich abwählen. Beim Zusammenführen werden nur Einstellungen übernommen, die hier noch auf der Vorgabe stehen. Mehrere Arten auf einmal werden in fester Reihenfolge übernommen: erst Maschinenprofile, dann Fräser, zuletzt Einstellungen – damit eine Standardmaschine aus den Einstellungen schon da ist.

Im Kasten *Gesicherte Stände im Portal* lässt sich jeder Stand einzeln **löschen** (mit Rückfrage).

## Was gesichert wird – und was nie

* **Maschinenprofile:** Name, Verfahrwege, Spindel- und Vorschubgrenzen, Zubehör, Taster, Kalibrierungen und Höhenkarte der Opferplatte, Notizen – ohne Pfade und Verbindungsdaten.
* **Meine Fräser:** Maße, Schnittwerte, Notizen deiner eigenen Bibliothek (nicht der mitgelieferte Katalog).
* **Einstellungen:** nur eine **feste Liste** von 22 Einstellungen, zum Beispiel Darstellung, Sprache, Fangen, Hinweise, Standardmaschine, Z-Null neuer Projekte. Eine neue Einstellung des Programms bleibt von selbst draußen, bis jemand sie bewusst aufnimmt.
* **Nie gesichert:** Token, Schlüssel und Passwörter (auch der API-Schlüssel des Assistenten und die Portal-Anmeldung), Verbindungsdaten (Anschlüsse, Adressen, Kamera), Dateipfade und freigegebene Ordner, zuletzt geöffnete Dateien, Fenstergröße und Aufteilung, Rechnerkennungen, Protokolle.

Die Sicherung liegt **privat in deinem Konto**; andere Konten sehen sie nicht. Sie liegt aber **unverschlüsselt in der Datenbank des Portals**, wie alle Kontodaten, und der Betreiber hat technisch Zugriff darauf. Verschlüsseln mit einem eigenen Schlüssel, automatisches Sichern und das Teilen einer Sicherung mit einem zweiten Konto gibt es nicht. Grenzen: 4 MiB je Stand, 64 MiB je Konto, höchstens 30 Anlegen oder Löschen pro Stunde. Löschst du dein Konto, werden auch die Sicherungen gelöscht; die Datenschutzerklärung des Portals nennt sie.

## Wenn es nicht klappt

| Meldung | Was du tun kannst |
|---|---|
| Das Portal sei zu alt / die Sicherung wird nicht angeboten | Das Portal muss Version 0.3.12 oder neuer laufen. Der Betreiber muss den Server aktualisieren. |
| Nicht angemeldet | Im Dialog anmelden (Geräte-Anmeldung wie in der Community). |
| »Alle Sicherungen des Kontos zusammen sind zu groß« | Nicht mehr benötigte Stände im Dialog löschen und erneut sichern. |
| »Zu groß« | Ein Stand überschreitet 4 MiB (viele Maschinen mit Höhenkarten): nicht benötigte Profile oder Fräser entfernen. |
| »Zu viele Anfragen« | Die angegebene Zeit abwarten. |

## Weiter

* [Maschine einrichten](Maschine-einrichten) – Profile, Liste, Standardmaschine, »Meine Maschine«
* [Werkzeuge und Schnittdaten](Werkzeuge-und-Schnittdaten) – Meine Bibliothek
* [Community-Portal](Community-Portal)
