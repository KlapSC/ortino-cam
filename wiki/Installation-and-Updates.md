**English** | [Deutsch](Installation-und-Updates)

# Installation and updates

ortino.CAM runs under **Windows 10 and 11 (64-bit)**. There is currently no version of the program for Mac or Linux. It is **free** for private and commercial use. The terms of use are in the file [LICENSE](https://github.com/KlapSC/ortino-cam/blob/main/LICENSE).

## Installing in four steps

1. **Download:** On the [release page](https://github.com/KlapSC/ortino-cam/releases/latest) the installer is available as `ortino.cam_<version>_x64-setup.exe`. Alternatively there is an `.msi` file (`…_x64_de-de.msi`). This documentation describes the published version **0.16.0**.
2. **Compare the checksum (recommended):** The SHA-256 checksum of each file is in the release notes of the version and in the file `SHA256SUMS.txt` on the release. You calculate it in Windows PowerShell like this and compare it with the stated value:

   ```powershell
   Get-FileHash .\ortino.cam_0.16.0_x64-setup.exe -Algorithm SHA256
   ```

3. **Start and install.** The installer sets the program up for your user (no administrator needed) and is available in German and English. The program needs Microsoft **WebView2**. If it is missing on your computer, the installer downloads it, so you need an internet connection then.
4. **Start.** `.ocam` projects then open with a double-click, as do `.ocamd` design packages from the [community portal](Community-Portal-en). An example project `tuerschild.ocam` comes with the releases (see [Getting started](Getting-Started)).

### Why does Windows warn (SmartScreen)?

On the first start Windows shows a blue warning (“Windows protected your PC”). The installer is signed with a **self-made certificate**, not one from a certificate authority, and Windows does not know this certificate. If you trust the installer, click **“More info”** and then **“Run anyway”**.

Trust the installer only if you downloaded it from the **official release page** and the **checksum matches**. A virus scanner may also flag the file `ortino-mcp.exe` (the MCP server for Claude, see [Claude, MCP and API](Claude-MCP-and-API)), because it is not signed individually.

## Updates

Updates come **inside the program itself**:

* If there is a new version, the **header bar** shows a notice.
* It is installed **only after your click**, with a verified signature and **never in the middle of a milling job** (the button is locked then). If there are unsaved changes, the program asks first.
* There are no downgrades. An installation through the `.msi` gets updates only as `.msi`, so that no second installation comes into being.
* Beforehand the installer closes the MCP server `ortino-mcp.exe` so that Claude Desktop does not block it. This is **not tested under Windows**. If the installer still reports that a file cannot be overwritten, close Claude Desktop and install again.

For this the program asks the **operator’s official portal**, **not GitHub**. Only the **type of operating system, architecture, type of installation and the installed version** are transmitted, no projects and no user data. The GitHub release page only shows the versions for manual download.

> **Honest about the status:** The updater is an early feature. Back up important projects before an update. If something goes wrong, you install the new version by hand from the release page.

## Where is your data?

Your machine profiles, your own cutter library, proven cutting data, the job log, custom post-processors and scripts are in the **data folder** `%APPDATA%\ortino.CAM` (the path is shown in the “About ortino.CAM” dialog). It is **outside the program folder**: an update or a reinstallation replaces only program files. This is **not tested with a real Windows update**. For a change of computer, or to be safe, copy the folder, or export machine profiles and cutter library through their dialogs. You save your project files (`.ocam`) wherever you like.

## What data does the program send?

* **Update query:** type of operating system, architecture, type of installation, installed version, to the operator’s portal.
* **Community portal:** You talk to it only when you use it.
* **Assistant in the program:** It talks to Anthropic when you switch it on with your own key.
* **Local interface:** off until you switch it on, and reachable only on `127.0.0.1`.
* **Camera:** images stay in working memory and are not saved or transmitted.
* **Phone remote control:** off at start.

## Requirements and notes

* **Window size:** at least 760 × 640 pixels (a tablet in portrait is enough), more comfortable from 1000 × 640.
* **3D view:** It needs WebGL. If the program shows “3D view unavailable”, update the graphics driver and switch on hardware acceleration. Checklist and job overview work without it.
* **Machine:** For the USB connection of the controller you need its USB driver (see [Setting up the machine](Setting-Up-the-Machine)).

## Uninstalling

Through the Windows settings (Apps) like any other program.

## Licence and liability

ortino.CAM is **not open-source software**. The source code is not public. The terms of use allow private and commercial use, but not passing on, modifying or reselling. Third-party components with their licences are listed in [THIRD-PARTY-NOTICES.txt](https://github.com/KlapSC/ortino-cam/blob/main/THIRD-PARTY-NOTICES.txt) and in the program under “About ortino.CAM → Licenses”. The program is provided without warranty, see the [disclaimer](https://github.com/KlapSC/ortino-cam/blob/main/README.en.md#disclaimer).

## Next

* [Getting started](Getting-Started)
* Problems with the installation: [Troubleshooting](Troubleshooting)
