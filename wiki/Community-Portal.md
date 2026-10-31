# Community-Portal

Neben dem Programm gibt es ein **Community-Portal**: eine Webseite, auf der Fräsdesigns gesammelt, durchsucht und geteilt werden, jeweils mit den Werkzeugen, Tiefen, Vorschüben und einer Anleitung, die zum Design gehören. Du erreichst es unter **[https://ortino-cam.com](https://ortino-cam.com)**. Im Programm ist diese Adresse schon eingetragen, du musst nichts einrichten.

![Community im Programm: Designseite mit „Laden & öffnen“, Lizenz und Beschreibung (Beispieldaten einer lokalen Installation)](https://raw.githubusercontent.com/KlapSC/ortino-cam/main/docs/bilder/community-im-programm-light.png)

> **Ehrlich zum Stand:** Das Portal wird von einer **Einzelperson** betrieben und ist **noch im Aufbau**. Das Zusammenspiel von Programm und Portal ist gegen eine lokale Testinstallation geprüft. Nicht alles ist im Betrieb im Internet erprobt, zum Beispiel »In ortino.CAM öffnen« aus dem Browser unter Windows, die Verknüpfung von `ortino://`-Links und `.ocamd`-Dateien mit dem Programm und die Anmeldung mit Google, Facebook oder Apple. Die Bilder auf dieser Seite zeigen **Beispieldaten aus einer lokalen Installation**, das Portal im Internet kann anders aussehen.
>
> **Schnittwerte in Designs** (Vorschub, Drehzahl, Tiefe) sind Angaben der Ersteller und gehören zu deren Maschine und Material. Prüfe sie vor dem Fräsen im Programm und beginne mit einem Reststück.

## Stöbern und suchen

Stöbern und Herunterladen gehen **ohne Konto**.

* **Entdecken:** Kategorien, Top Picks, Im Trend, Neu, Beliebt.
* **Suche:** verzeiht Tippfehler, macht Vorschläge beim Tippen und filtert nach Kategorie, Art, Material, Plattenstärke, Fräser und Lizenz.
* **»Passt auf meine Maschine«:** vergleicht den Verfahrweg der Maschine in deinem offenen Projekt mit dem Design (auch um 90° gedreht). Karten und Designseite zeigen »passt«, »passt gedreht« oder »zu groß«.
* **Designseite:** Galerie, Beschreibung, Anleitung, die Einstellungen (Arbeitsbereich, Material, Dicke, Zeit, Werkzeuge, Bearbeitungen mit Tiefe, Vorschub und Drehzahl), Zusatzdateien und Kommentare. Kommentieren geht im Browser.

![Startseite des Community-Portals mit Suche (Beispieldaten einer lokalen Installation)](https://raw.githubusercontent.com/KlapSC/ortino-cam/main/docs/bilder/portal-startseite-light.png)

## Im Programm laden und öffnen

1. Öffne die Community über die **Weltkugel in der Kopfleiste**, mit `Strg+Umschalt+D`, über das Menü Extras (»Community-Designs entdecken«) oder die Befehlspalette (`Strg+K`, »Community«).
2. Wähle ein Design und klicke **»Laden & öffnen«** (oder »Nur laden«).
3. Das Programm prüft das Paket, **bevor** du es öffnest: Die Prüfsumme muss stimmen, Pfade im Paket dürfen nicht aus dem Ordner herausführen, Größen und Kompression müssen plausibel sein, und **ausführbare Inhalte werden abgelehnt**. Ein Paket ist höchstens 150 MB groß. Skripte aus Paketen werden **nie** ausgeführt, und aus einem Paket wird nie eine Maschinenaktion ausgelöst.
4. Danach wählst du: **Als neues Projekt öffnen** (bei ungespeicherten Änderungen fragt das Programm zuerst) oder **In das aktuelle Projekt einfügen**. Beim Einfügen kommen nur die **Formen** (Umrisse) der Platte mittig auf die aktive Platte, als ein Rückgängig-Schritt. **Bearbeitungen, Werkzeuge und Variablen werden dabei nicht übernommen**, Texte kommen als Pfade.
5. Geladene Designs bleiben unter **»Meine geladenen«**. »Auf neue Versionen prüfen« zeigt, ob es eine neuere Fassung gibt. Zusatzdateien und Bilder eines Pakets kannst du speichern.

**Welche Maschine gilt?** Ein Design trägt eine Kopie der Maschine seines Erstellers. Ab Version 0.3.12 öffnet ortino.CAM es standardmäßig mit **deiner eigenen Maschine** (Standardmaschine, mit Postprozessor, Zubehör, Taster und Kalibrierung); Platten, Material, Bearbeitungen und Werkzeuge des Designs bleiben. Über dem Knopf »Als neues Projekt öffnen« kannst du **»Die des Designs«** wählen (Name, Maße und Postprozessor); Taster, Wechselposition und Höhenkarte einer fremden Maschine werden **auch dann nie** übernommen. Nach dem Öffnen steht in der Meldung, womit geöffnet wurde, und ein Hinweis, wenn das Design größer ist als der Verfahrweg deiner Maschine.

Eine `.ocamd`-Datei (so heißt ein Designpaket) öffnest du auch per Doppelklick oder über »Paket öffnen …«. Das Portal bietet außerdem »In ortino.CAM öffnen« als Link. Ein solcher Link **lädt nie sofort**: Zuerst erscheint eine Bestätigung mit Portal-Adresse, Designname und Autor. Ein unbekanntes Portal wird gar nicht erst angefragt, bis du ihm ausdrücklich vertraust.

## Neue Adresse (seit 0.7.0)

Das Portal ist umgezogen: Es liegt jetzt unter **[ortino-cam.com](https://ortino-cam.com)**, früher unter `benini.access.ly:8088`. ortino.CAM ab Version 0.7.0 hat die neue Adresse schon eingetragen. Ältere Programmversionen fragen für ihr Update noch eine Übergangszeit bei der alten Adresse nach; nach dem Update zeigen sie auf die neue. Dein Konto und deine Designs sind mitgekommen. Weil die Adresse neu ist, musst du dich **einmal neu anmelden** (Browser und Programm). Alte Links aus E-Mails zeigen auf die alte Adresse und führen für diese Übergangszeit nur auf einen Umzugshinweis.

## Anmelden

Zum Teilen brauchst du ein **kostenloses Konto**. Die Anmeldung im Programm läuft wie am Fernseher über einen Code: ortino.CAM zeigt dir einen kurzen Code und öffnet die Bestätigungsseite des Portals im Browser. Dort meldest du dich an und bestätigst das Gerät. **ortino.CAM sieht dein Passwort nie.** Der Zugangsschlüssel für dein Konto liegt unter Windows im Windows-Anmeldeinformationsspeicher, nicht in Dateien. »Abmelden« löscht ihn auf diesem Rechner.

## Eigene Designs teilen

Der Assistent **»Design teilen«** (Community → Teilen) teilt immer das **offene Projekt**.

1. **Angaben:** Titel, Kategorie, Kurzbeschreibung, Beschreibung, Anleitung, Schlagwörter, Lizenz.
2. **Bilder:** ein Vorschaubild entsteht automatisch, dazu kannst du eigene Fotos anhängen (PNG, JPEG oder WebP, höchstens acht). Eigene Bilder bekommen neutrale Namen.
3. **Prüfen:** Du siehst, was veröffentlicht wird, samt den Angaben aus dem Projekt. Die **Datenschutzprüfung** sucht im Projekt nach Dateipfaden und deinem Benutzernamen. »Automatisch entfernen« ersetzt sie **nur im Paket**, dein Projekt bleibt unverändert. Inhalte von Formen (zum Beispiel ein Schildtext) ändert das Programm nie. Hier musst du bewusst bestätigen. Ohne Bereinigung oder Bestätigung wird nichts hochgeladen.
4. **Hochladen:** Sichtbarkeit **Öffentlich**, **Nicht gelistet** oder **Entwurf**.

Ab Version 0.3.12 kommen die **Einrichtung deiner Maschine** (Zubehör, fester Taster, Opferplatte, Kamera) und die **freie Notiz der Maschine** nicht mehr ins Paket; Name, Verfahrwege und Postprozessor bleiben als Information. Bereits veröffentlichte Pakete lassen sich nicht ändern: Hast du früher ein Design geteilt, kann es die Notiz noch enthalten – dann zurückziehen und neu teilen.

Unter **Meine Designs** bearbeitest du Angaben, lädst neue Versionen hoch, veröffentlichst, ziehst zurück (das Design wird dann »nicht gelistet«) oder löschst. Auch Vorlagen mit Eingabeformular (siehe [Platten und Möbel](Platten-und-Möbel)) lassen sich als Design teilen. Mehr zum Thema Teilen durch Claude: [Claude, MCP und API](Claude-MCP-und-API).

## Rechte, Lizenzen und Richtlinien

* Lade nur hoch, was du **selbst erstellt hast oder teilen darfst**.
* Jedes Design trägt eine **Lizenz**: CC BY (Namensnennung), CC BY-SA (zusätzlich Weitergabe unter gleichen Bedingungen), CC BY-NC (nicht kommerziell), CC BY-NC-SA, CC BY-ND (keine Bearbeitung), CC0 (keine Einschränkung) oder »Alle Rechte vorbehalten«. Das ist eine Kurzfassung und keine Rechtsberatung. Maßgeblich sind die Lizenztexte, die zum Design angezeigt werden.
* Laut Community-Richtlinien **nicht erlaubt** sind: fremde Werke ohne Erlaubnis, geschützte Logos und Marken, Waffen oder rechtlich eingeschränkte Teile, gefährliche Anleitungen, absichtlich falsche Einstellungen und Schadsoftware.
* Verstöße meldest du über **»Melden«** bei der Moderation.

## Küche und Möbel im Browser

Seit Version 0.5.0 laufen der Küchen- und der Möbel-Designer auch im Portal, ohne Installation, mit Entwürfen im eigenen Konto und Download als `.ocam` für das Programm; seit 0.6.0 lassen sich Entwürfe teilen und abwechselnd bearbeiten, seit 0.7.0 auf Wunsch des Besitzers auch gleichzeitig (live). Das ist eine eigene Anleitung: [Web-Designer im Portal](Web-Designer-im-Portal). Es braucht ein Konto mit bestätigter E-Mail-Adresse und ein Portal ab Server-Version 0.5.0.

## Boosts und Punkte (seit 0.7.0)

Jedes Konto mit bestätigter E-Mail-Adresse, das mindestens drei Tage alt ist, kann je **Kalendermonat** (Zeitzone Europe/Zurich) **4 Boosts** an Designs **anderer** verteilen: einmal je Design, höchstens zwei an denselben Ersteller, nie an eigene Designs. Nicht verteilte Boosts verfallen am Monatsende; einen Boost kannst du kurz nach dem Vergeben zurücknehmen. Wer ein Design erstellt hat, bekommt je Boost **Punkte**: zuerst vorgemerkt, nach 14 Tagen verfügbar. Öffentlich sichtbar ist nur die **Anzahl** der Boosts, wer geboostet hat, sehen nur Moderation und Administration. **Punkte sind kein Geld, nicht übertragbar und nicht auszahlbar; einen Shop gibt es noch nicht.** Bei Missbrauch werden Punkte zurückgebucht. Der Betreiber kann das Programm abschalten (`ORTINO_HUB_BOOST=off`). Nur gegen lokale Server und Chromium geprüft, nie mit echten Nutzern.

## Maschinenprofile aus der Community (seit 0.7.0)

Konten können die **technischen Angaben** ihrer Fräse (Hersteller, Modell, Steuerung, Firmware, Verfahrweg, Spindel, Vorschub, Eilgang, Beschleunigung, Postprozessor, Referenzecke) als Profil veröffentlichen, nicht Kalibrierung, Tasterlage, Pfade oder Namen. Andere finden es im Portal oder im Programm (`Strg+K` → *Maschine aus dem Portal*), **laden** es (es überschreibt nie dein Profil und ist als »ungeprüft« gekennzeichnet) und können mit einem Klick **»läuft bei mir«** sagen. **»Bestätigt von n Nutzern«** ist eine Angabe von Konten, **keine Prüfung durch ortino.CAM**: Vergleiche die Werte vor dem ersten Einsatz mit dem Handbuch deiner Maschine. Bestätigen dürfen nur andere Konten mit bestätigter Adresse, die mindestens 24 Stunden alt sind.

## Marktplatz (seit 0.8.0, standardmäßig aus)

Das Portal kann **Designs** und **Schnittdaten-Sätze** (Vorschub, Drehzahl und Zustellung je Fräser und Material) gegen **Punkte** anbieten. Punkte sind **keine Währung**: Es gibt kein Geld und keinen Zahlungsanbieter. Die Verkäuferin oder der Verkäufer bekommt 90 % des Preises, **10 % verfallen**; die Gutschrift kommt nach einer Wartezeit von 14 Tagen. Eine **Rückgabe gibt es nicht**, eine Erstattung nur bei einem Mangel (Datei defekt oder Inhalt anders als beschrieben), nach Prüfung durch die Moderation und innerhalb von 30 Tagen. Verkaufen dürfen nur Konten mit bestätigter E-Mail-Adresse, die die Moderation einmal freigeschaltet hat; jedes bezahlte Angebot wird vor der Veröffentlichung geprüft. Titel, Beschreibung, Bilder und Vorschau sind frei sichtbar, die Dateien und Werte erst nach dem Kauf.

**Der Marktplatz ist auf einem neuen Portal ausgeschaltet.** Der Betreiber kann ihn erst einschalten, wenn er bestätigt hat, dass die Rechtstexte geprüft sind; die mitgelieferten Texte sind **Entwürfe ohne Prüfung durch eine Fachperson**. Das Windows-Programm kann bezahlte Designs **nicht kaufen**: Es zeigt eine Meldung mit Link zum Kauf im Browser. Ein Verkäufer-Konto lässt sich erst löschen, wenn die Erstattungsfristen seiner Verkäufe abgelaufen sind. Nichts davon ist mit echten Nutzern erprobt.

## Sicherung im Portal

Mit einem Konto kannst du Maschinenprofile, eigene Fräser und ausgewählte Einstellungen privat sichern und auf einem anderen Rechner abrufen. Das ist eine eigene Anleitung: [Sicherung im Portal](Sicherung-im-Portal).

## Der Katalog eigener Designs

Als Grundstock ist ein Katalog mit **17 eigenen Beispiel-Designs** vorbereitet: Leuchten, Wandbilder, Stühle und Tische. Sie stammen vom KI-Konto »Claude«, wurden **nur am Rechner geprüft** (Prüfliste, G-Code, Simulation) und **nie gefräst oder belastet**. Bei Möbeln baust du erst einen Prototyp.

## Wenn es nicht klappt

| Meldung | Was du tun kannst |
|---|---|
| »Keine Verbindung zum Portal …« | Internetverbindung prüfen. Ist ein Firmen-Proxy im Weg, brauchst du dessen Einstellung. ortino.CAM arbeitet ohne Portal normal weiter. |
| »Zeitüberschreitung …« | Später erneut versuchen, bei großen Dateien auf eine stabile Verbindung achten. |
| »Sichere Verbindung … fehlgeschlagen (Zertifikat)« | Die Uhrzeit deines Rechners prüfen. Bleibt es, melde es über GitHub Issues. |
| »Die Anmeldung … ist abgelaufen oder wurde widerrufen« | Erneut anmelden. Stöbern geht auch ohne Anmeldung. |
| »Dafür fehlt die Berechtigung« | Richtiges Konto? Zum Veröffentlichen muss deine E-Mail-Adresse im Portal bestätigt sein. |
| »Nicht gefunden …« | Das Design wurde gelöscht, zurückgezogen oder ist nicht öffentlich. |
| »Zu viele Anfragen … In N s erneut versuchen« | Die angegebene Zeit abwarten. |
| »Das Designpaket wurde abgelehnt …« | Das Paket ist defekt oder manipuliert. Nicht verwenden, den Autor informieren oder melden. |
| »… beschädigt (Prüfsumme stimmt nicht)« | Erneut laden. |
| »Das Paket enthält Dateipfade oder Ihren Benutzernamen« | Im Schritt »Prüfen« automatisch entfernen lassen oder bewusst bestätigen. |

Unter *Konto & Portale → Fehlersuche → Protokoll anzeigen* siehst du die Abläufe ohne Zugangsdaten und Inhalte.

## Kontakt

Fragen, Fehler und Wünsche zum Portal gehen wie überall über [GitHub Issues](https://github.com/KlapSC/ortino-cam/issues/new/choose). Issues sind öffentlich: Schreib dort keine persönlichen Daten hinein. **Datenschutzanfragen und rechtliche Anliegen** zum Portal (Konto, Auskunft, Löschung, Sperre, Widerspruch gegen eine Entscheidung der Moderation) gehen an die E-Mail-Adresse im [Impressum des Portals](https://ortino-cam.com/imprint). Fräsdesigns (Schilder, Möbel, Muster) gehören ins Portal und nicht in das öffentliche Repository.

<!-- videos:start -->
## Videos (English)

* [![Find a design in the community portal (video, English captions)](https://klapsc.github.io/ortino-cam/videos/portal-browse-poster.jpg)](https://klapsc.github.io/ortino-cam/videos/#portal-browse)  
**Find a design in the community portal** · 14 s

* [![Share your own design in the community portal (video, English captions)](https://klapsc.github.io/ortino-cam/videos/portal-share-poster.jpg)](https://klapsc.github.io/ortino-cam/videos/#portal-share)  
**Share your own design in the community portal** · 18 s

Alle Videos: [Videos](Videos).
<!-- videos:end -->
