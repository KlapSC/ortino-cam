**English** | [Deutsch](Fehlersuche)

# Troubleshooting

Here are common problems with the cause and a solution. For every problem at the machine this applies: **When in doubt, press the emergency stop, do not first press “Stop” in the software.** Messages in the program usually name a solution themselves (“Solution: …”). Read it first. If you find nothing here, ask via [GitHub Issues](https://github.com/KlapSC/ortino-cam/issues/new/choose) (see [Contributing and Testing](Contributing-and-Testing)).

## Installation and program

| Problem | Cause and solution |
|---|---|
| **Windows warns during installation** (SmartScreen) | The installer is signed with a self-made certificate. If you have it from the official release page and the checksum matches: “More info” → “Run anyway”. See [Installation and Updates](Installation-and-Updates). |
| “3D view unavailable” or “WebGL is not available” | The graphics driver does not provide WebGL. Update the driver, switch on hardware acceleration, restart ortino.CAM. The checklist and the job overview also work without it. |
| Installation or update reports that a file cannot be overwritten | Usually Claude Desktop keeps `ortino-mcp.exe` locked. Quit Claude Desktop and install again. |
| Error texts in the English interface are in German | Known limitation (also in 0.8.2): Since 0.8.2 the core delivers names, G-code comments, console, alarms and checklist in the language of the interface. Most error messages of the kitchen designer, warnings of the operations, many error texts and individual part checks are still in German. |
| “Backup in the portal” reports that the portal is too old, or does not offer it | The backup needs a portal from version 0.3.12. The operator of the portal has to update the server; until then everything else works as before. See [Backup in the Portal](Backup-in-the-Portal). |
| Work is missing after a crash | At the start the welcome page offers to restore the automatically saved state. Save it under a name afterwards. |

## Connection to the machine

| Problem | Cause and solution |
|---|---|
| **No COM port in the list** | Switch on the controller, check the cable and “Refresh ports”. If something is still missing, the USB driver is missing (for the xPRO V5 the CP210x from Silicon Labs, for other controllers often CH340 or FTDI). According to the manufacturer a USB-C to USB-C cable does not work with the xPRO V5, use USB-A to USB-C. |
| **No reply after connecting** | Wrong baud rate (GRBL default and xPRO V5: 115200) or the controller is still restarting. When the port is opened, the xPRO V5 restarts, the message `Grbl …` in the console is normal. Connect again. |
| Status bar: **“No reply for … s”** | Check cable and power supply, disconnect and reconnect if necessary. After 8 seconds of silence during a job the program holds the feed. |
| **Connection drops in the middle of a job** | The most common cause is the USB power saving of Windows. In the power options disable “USB selective suspend”, in the Device Manager clear “Allow the computer to turn off this device …” for the USB hubs and the COM port, switch off sleep during long jobs, keep the USB cable short and route it separately from motor and spindle cables. After an abort a notice shows the last confirmed line and offers “Start at line”. Check homing and work zero beforehand. |
| Network connection does not work | Enter the address as `address:port` (for example `192.168.1.50:23`). |

## Alarm, homing and direction of travel

| Problem | Cause and solution |
|---|---|
| **Alarm** in the card | The controller is locked. Remove the cause, then **Unlock (`$X`)**, **Home (`$H`)** or **Reset**. **After an alarm the position may be lost.** Check the work zero before you mill. |
| An alarm has stopped the job | It cannot be continued, because the controller has switched off spindle and dust extraction and discarded the buffer. Abort the job, check work zero and tool, then restart with “Start at line”. |
| Alarm 2 (soft limit) in the middle of a job | A move would have exceeded the travel. The pre-flight check checks this in advance. Read its errors, and check the travel in the machine profile and `$130–$132` ([Setting Up the Machine](Setting-Up-the-Machine)). |
| Homing goes to the wrong corner | Check `$23` (direction) and `$3` (axis direction). The setup assistant derives the corner from `$23`. |
| An axis moves the wrong way round | Axis test in the assistant, change the `$3` mask or reverse the motor cable of the axis. Correct is +X to the right, +Y to the back, +Z up. |
| The manual control does not move | It is locked as long as the machine is not ready (alarm, not idle) or a program is running. The reason is shown in the card. |
| “Start blocked” | The pre-flight check has found errors (for example no homing, travel exceeded, alarm, checklist with errors). Errors cannot be clicked away, fix them. You confirm warnings one by one with “Understood”. |

## Work zero and probing

| Problem | Cause and solution |
|---|---|
| **Probing fails:** “no contact” (alarm 5) | The bit touched nothing in the search path. Check that the clip is on the bit, the lead is plugged into the probe input and the touch plate or corner block is clean. With **“Test probe input”** you check lead and contact. If necessary increase the “Max. depth”. Then unlock (`$X`) and probe again. The work zero stays unchanged. |
| Probing: **alarm 4**, probe already triggered | The probe input reports contact already before the start. Lift the bit, check clip and lead (short circuit?). Probing stays locked until the input is open. |
| The “Probe input” indicator stays “unknown” | Some firmware does not report the pin state. Then only a dry test with the probing itself remains. |
| Probing locked: material thickness unknown | If Z zero is set to “Table (spoilboard)”, the card needs the material thickness. Check the thickness in the sheet settings in the “Project” step. The program does not guess. |
| **The workpiece is milled too deep or not at all** | Check Z zero: **Top of sheet** or **Table (spoilboard)** in the project, and the thickness of the touch plate (does it lie on the workpiece or on the spoilboard?). Run an **air cut** beforehand and check Z0 with a sheet of paper: after setting Z0 the bit must be standing on the surface. |
| X/Y work zero is at the wrong corner | With the corner block choose the corner in the card to match the work zero of the sheet (the note in the card warns). The centre as work zero cannot be probed with the corner block. |

## Dimensions and toolpaths

| Problem | Cause and solution |
|---|---|
| **Dimensions are wrong** (part too large or too small) | Several causes: (1) **Import** with the wrong scale. For SVG 1 px = 0.2646 mm (96 dpi) applies, for files from programs with 72 dpi the quick choice “72 → 96 dpi ×1.33” helps. (2) **Steps per millimetre** of the controller: move 100 mm as a test and measure, check `$100–$102`. (3) **Inch reports** (`$13=1`) distort positions by a factor of 25.4. (4) The **bit diameter** in the project differs from the real one. |
| Joints (fingers, slots) do not fit | Measure the real thickness and mill the **test coupon**, see [Sheets and Furniture](Sheets-and-Furniture). The program does not know about material swelling and bit wear. |
| **“Toolpath cannot be calculated”** | The message names the cause and a solution. Often: no shapes assigned (“Use selection”), pocket on an **open** shape (close or join the path), end depth not deeper than start depth, depth per pass 0, unknown variable (create it under “Project → Variables”), shape on another sheet or an invalid tool (correct it under “Manage tools”). |
| Paths are missing or the operation shows “empty” | The geometry check shows open or duplicate contours, self-intersections and inside radii that are too tight. With V-carving a clearing tool may be too large for the flat bottom, the message names a depth as a way out. |
| Paths look **wrong**: The bit cuts inside instead of outside | For a profile check the **side** (Outside, Inside, On line). Outside means: the part inside the contour keeps its size. |
| Inside corners become round | A round bit cannot mill a sharp inside corner. Use the relief of inside corners (dogbone), a smaller bit or allow for it. |
| Parts come loose when cutting through or fly away | Tabs are missing. The checklist and the hints report this for cut-throughs. |
| **Edge rough or burnt** | Check feed rate and spindle speed (they are guide values!). With wood or plastic **climb milling** can be cleaner, see [Operations](Operations). The hint “Chip too thin – burn risk” suggests the guide value. If you have set a tool-life limit for the bit, the pre-flight check reports when it is reached ([Tools and Cutting Data](Tools-and-Cutting-Data)). |
| Export locked | The checklist has **errors**. Errors cannot be accepted, warnings can. Read the solution on the entry. |
| Rapid moves into standing material | The checklist reports this as an error. Create an operation beforehand that clears down to this depth, or set the start depth to 0. |

## Camera on the worktable

| Problem | Cause and solution |
|---|---|
| **The camera does not find the markers** | (1) Markers too small in the image: move closer, higher resolution or larger markers (up to 100 mm). (2) Noisy, blurred or reflective: even, soft light, markers printed matt, no backlight. (3) Markers cut off at the edge of the image: align the camera so that all four are completely in the image. (4) At least three markers must be usable, four are better. (5) The sheet was not printed at 100%: check the 100 mm scale. (6) Markers from different sheets or duplicates: one sheet, each number once. |
| “Assignment not unambiguous” | The program does not guess. Often the image is mirrored, or the markers are not in the corners. |
| The image does not match the design | Parallax: the markers must lie at the height of the material surface. If the camera was knocked, calibrate again. |
| The camera icon is missing in the header bar | In narrow windows (under 1180 pixels in width) the icon is omitted so that it does not overlap the “Cut” step. The camera stays reachable via `Ctrl+K`, the tool palette in the “Design” step and the status bar. |
| Access to the camera is denied | **Settings → Privacy & security → Camera:** switch on “Camera access”, “Let apps access your camera” and “Let desktop apps access your camera”. This has not yet been checked under Windows. With “Image from file …” it also works without a camera. |

More on this on [Camera on the Worktable](Camera-on-the-Worktable).

## Phone, Claude and portal

* **Phone remote control:** See the table “If it does not work” on [Phone Remote Control](Phone-Remote-Control) (firewall, same Wi-Fi, code expired, connection unstable).
* **Claude does not appear in Claude Desktop:** See [Claude, MCP and API](Claude-MCP-and-API).
* **Portal:** “No connection to the portal …” and further messages are listed with a solution under [Community Portal](Community-Portal-en). ortino.CAM keeps working normally without the portal.

## Nothing helps?

Report it as an issue. State the version, the Windows version, what you did and what you expected. For problems at the machine state the machine and controller and attach the excerpt from the console. Please **no personal data**. You do **not** report security vulnerabilities as a public issue (see the [security policy](https://github.com/KlapSC/ortino-cam/blob/main/SECURITY.md)).
