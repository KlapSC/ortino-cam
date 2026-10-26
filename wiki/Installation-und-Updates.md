# Installation und Updates

ortino.CAM läuft unter **Windows 10 und 11 (64 Bit)**. Für Mac und Linux gibt es das Programm derzeit nicht. Es ist **kostenlos** für private und gewerbliche Nutzung. Die Nutzungsbedingungen stehen in der Datei [LICENSE](https://github.com/KlapSC/ortino-cam/blob/main/LICENSE).

## Installieren in vier Schritten

1. **Herunterladen:** Auf der [Release-Seite](https://github.com/KlapSC/ortino-cam/releases/latest) liegt der Installer als `ortino.cam_<Version>_x64-setup.exe`. Alternativ gibt es eine `.msi`-Datei (`…_x64_de-de.msi`). Diese Dokumentation beschreibt die veröffentlichte Version **0.3.12**.
2. **Prüfsumme vergleichen (empfohlen):** Die SHA-256-Prüfsumme jeder Datei steht in den Hinweisen der Version und in der Datei `SHA256SUMS.txt` am Release. Du berechnest sie in der Windows-PowerShell so und vergleichst sie mit der Angabe:

   ```powershell
   Get-FileHash .\ortino.cam_0.4.1_x64-setup.exe -Algorithm SHA256
   ```

3. **Starten und installieren.** Der Installer richtet das Programm für deinen Benutzer ein (kein Administrator nötig) und gibt es auf Deutsch und Englisch. Das Programm braucht Microsofts **WebView2**. Fehlt es auf deinem Rechner, lädt der Installer es dafür nach, du brauchst dann eine Internetverbindung.
4. **Starten.** `.ocam`-Projekte öffnen sich danach per Doppelklick, ebenso `.ocamd`-Designpakete aus dem [Community-Portal](Community-Portal). Ein Beispielprojekt `tuerschild.ocam` liegt den Releases bei (siehe [Erste Schritte](Erste-Schritte)).

### Warum warnt Windows (SmartScreen)?

Beim ersten Start zeigt Windows eine blaue Warnung (»Der Computer wurde durch Windows geschützt«). Der Installer ist mit einem **selbst erstellten Zertifikat** signiert, nicht von einer Zertifizierungsstelle, und Windows kennt dieses Zertifikat nicht. Wenn du dem Installer vertraust, klickst du auf **»Weitere Informationen«** und dann auf **»Trotzdem ausführen«**.

Vertraue dem Installer nur, wenn du ihn von der **offiziellen Release-Seite** geladen hast und die **Prüfsumme stimmt**. Auch ein Virenscanner kann die Datei `ortino-mcp.exe` (der MCP-Server für Claude, siehe [Claude, MCP und API](Claude-MCP-und-API)) melden, denn sie ist nicht einzeln signiert.

## Updates

Updates kommen **im Programm selbst**:

* Gibt es eine neue Version, zeigt die **Kopfleiste** einen Hinweis.
* Installiert wird **nur nach deinem Klick**, mit geprüfter Signatur und **nie mitten in einem Fräsauftrag** (der Knopf ist dann gesperrt). Bei ungespeicherten Änderungen fragt das Programm zuerst.
* Es gibt keine Downgrades. Eine Installation über die `.msi` bekommt Updates nur als `.msi`, damit keine zweite Installation entsteht.
* Der Installer beendet vorher den MCP-Server `ortino-mcp.exe`, damit Claude Desktop ihn nicht blockiert. Das ist **nicht unter Windows erprobt**. Meldet der Installer trotzdem, eine Datei könne nicht überschrieben werden, beende Claude Desktop und installiere erneut.

Das Programm fragt dafür beim **offiziellen Portal des Betreibers** an, **nicht bei GitHub**. Übermittelt werden nur **Systemart, Architektur, Installationsart und die installierte Version**, keine Projekte und keine Nutzerdaten. Die GitHub-Release-Seite zeigt nur die Versionen zum manuellen Herunterladen.

> **Ehrlich zum Stand:** Der Updater ist eine frühe Funktion. Sichere wichtige Projekte vor einem Update. Geht etwas schief, installierst du die neue Version von Hand über die Release-Seite.

## Wo liegen deine Daten?

Deine Maschinenprofile, die eigene Fräserbibliothek, bewährte Schnittdaten, das Job-Protokoll, eigene Postprozessoren und Skripte liegen im **Datenverzeichnis** `%APPDATA%\ortino.CAM` (im Dialog »Über ortino.CAM« steht der Pfad). Es liegt **außerhalb des Programmordners**: Ein Update oder eine Neuinstallation ersetzt nur Programmdateien. Das ist **nicht mit einem echten Windows-Update erprobt**. Für einen Rechnerwechsel oder zur Sicherheit kopierst du das Verzeichnis, oder du exportierst Maschinenprofile und Fräserbibliothek über ihre Dialoge. Deine Projektdateien (`.ocam`) speicherst du, wo du möchtest.

## Welche Daten sendet das Programm?

* **Update-Abfrage:** Systemart, Architektur, Installationsart, installierte Version, an das Portal des Betreibers.
* **Community-Portal:** Du sprichst nur mit ihm, wenn du es benutzt.
* **Assistent im Programm:** Er spricht mit Anthropic, wenn du ihn mit deinem eigenen Schlüssel einschaltest.
* **Lokale Schnittstelle:** aus, bis du sie einschaltest, und nur auf `127.0.0.1` erreichbar.
* **Kamera:** Bilder bleiben im Arbeitsspeicher und werden nicht gespeichert oder übertragen.
* **Handy-Fernbedienung:** aus beim Start.

## Voraussetzungen und Hinweise

* **Fenstergröße:** mindestens 760 × 640 Pixel (ein Tablet im Hochformat reicht), bequemer ab 1000 × 640.
* **3D-Ansicht:** Sie braucht WebGL. Zeigt das Programm »3D-Ansicht nicht verfügbar«, aktualisiere den Grafiktreiber und schalte die Hardwarebeschleunigung ein. Prüfliste und Auftragsübersicht funktionieren auch ohne.
* **Maschine:** Für den USB-Anschluss der Steuerung brauchst du deren USB-Treiber (siehe [Maschine einrichten](Maschine-einrichten)).

## Deinstallieren

Über die Windows-Einstellungen (Apps) wie jedes andere Programm.

## Lizenz und Haftung

ortino.CAM ist **keine Open-Source-Software**. Der Quelltext ist nicht öffentlich. Die Nutzungsbedingungen erlauben private und gewerbliche Nutzung, aber nicht Weitergeben, Verändern oder Weiterverkaufen. Bausteine Dritter mit ihren Lizenzen stehen in [THIRD-PARTY-NOTICES.txt](https://github.com/KlapSC/ortino-cam/blob/main/THIRD-PARTY-NOTICES.txt) und im Programm unter »Über ortino.CAM → Lizenzen«. Das Programm wird ohne Gewährleistung bereitgestellt, siehe den [Haftungsausschluss](https://github.com/KlapSC/ortino-cam#haftungsausschluss).

## Weiter

* [Erste Schritte](Erste-Schritte)
* Probleme bei der Installation: [Fehlersuche](Fehlersuche)
