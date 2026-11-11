**English** | [Deutsch](Claude-MCP-und-API)

# Claude, MCP and API

ortino.CAM can be controlled from outside: by **Claude** (Claude Desktop, Claude Code or any other program that speaks the *Model Context Protocol*, **MCP** for short), by your own programs through a **local interface (API)**, and from the **command line** `ortino`. There are also small **scripts** and an **assistant in the program**.

**You do not need any of this.** Everything essential works without Claude and without an Anthropic key. This page is for anyone who wants to try it.

> **Honest about the status:** The program is an early version, and the Claude connection can have bugs like everything else in it. Machine commands via Claude or the interface are, like all machine functions, only checked against the simulator (except what is listed as tested on [Milling on the machine](Milling-on-the-Machine)). According to the documentation (as of October 2026), the assistant in the program was only tested against a replica server, not against the real Anthropic interface. The machine's emergency stop remains the last safeguard. See the [disclaimer](https://github.com/KlapSC/ortino-cam/blob/main/README.en.md#disclaimer).

## The MCP server `ortino-mcp`

With the MCP server, Claude and other clients can draw, create operations, work through the checklist and generate G-code, **live in the program window**. Every action is an undo step (“KI: 3 Formen anlegen”, Ctrl+Z takes it back). The program `ortino-mcp.exe` comes with the Windows installer, next to `ortino.CAM.exe`.

### Setting up

1. **Turn on external control (recommended):** Extras → *Extensions & AI …* → **Allow external control**. ortino.CAM then starts an interface that can be reached **only on this computer** (`127.0.0.1`) with a random access key. The status bar shows “External control”. Without this step `ortino-mcp` works **standalone** with its own project in memory, and the program window sees none of it.
2. **Claude Desktop:** *Settings → Developer → Edit Config* opens the file `claude_desktop_config.json`. Add the entry (ortino.CAM shows the right path to copy under *Extensions & AI → Connect Claude*):

   ```json
   {
     "mcpServers": {
       "ortino-cam": {
         "command": "C:\\Users\\<Name>\\AppData\\Local\\ortino.CAM\\ortino-mcp.exe",
         "args": []
       }
     }
   }
   ```

   Backslashes are doubled in JSON. If there are other servers already, add only the block `"ortino-cam": { … }`. Then **restart** Claude Desktop. ortino.CAM appears among the tools.
3. **Claude Code:** `claude mcp add --scope user ortino-cam -- "C:\Users\<Name>\AppData\Local\ortino.CAM\ortino-mcp.exe"`. With `/mcp` you check whether “ortino-cam” is connected.
4. **Try it:** Ask Claude, for example: “In ortino.CAM, design a door sign 300 × 150 mm with the text ‘Workshop’, four mounting holes Ø5 and an outer contour with tabs. Check the result and show me a preview image.” Claude then uses tools such as `get_project`, `create_shapes`, `add_operation`, `run_checklist` and `render_preview`.

Options for `"args"` (selection): `--attach` (only attach to the running program), `--headless` (always standalone), `--project <file>` (standalone with this file), `--readonly` (read-only tools only), `--allow-machine` and `--allow-danger` (see below), `--lang de` (tool descriptions in German), `--log <file>` (write all messages to a log), `--check` (check the connection).

### What Claude can do

There are deliberately few, tailored tools: read and change the project, create and change shapes (including Boolean operations, rounding corners, editing nodes, sheet planner), create and change operations, manage tools, checklist, simulation and preview image, suggestions for cutting values, fill in templates, import and export SVG/DXF. `list_api_methods` lists all methods of the interface; they can be called with `call_api`. Numbers are millimetres, lengths may be formulas (`Breite/2 - 5mm`) and then stay parametric.

**Creators (since 0.13.0):** Claude can use the [Creators](Creators) through `call_api` (`creator.list`, `creator.info`, `creator.preview`, `creator.create`); the preview changes nothing, creating is one undo step. Claude also knows the [order of the depth passes](Operations) when it creates and changes operations. Customer records and quotes are **not reachable** for Claude.

**Files:** Claude has no access to your hard disk. It may read only from **allowed read folders** (the folder of the saved project, `Documents\ortino.CAM` and folders you allow under *Extensions & AI → Connect Claude*). It may write only to **output folders**, only with a matching file extension and never to system folders. Alternatively you hand over content as text or upload large files in parts.

## The four safety levels

Everything that comes from outside is assigned to one level:

| Level | What is allowed | Default |
|---|---|---|
| `read` | Read project, checklist, preview, simulation | allowed |
| `edit` | Change the project in memory. Every action is exactly one undo step; if there is an error, everything stays unchanged. | allowed (except with `--readonly`) |
| `machine` | Jogging, spindle, work zero, homing, probing, connecting | **blocked**, every action needs confirmation in the program |
| `danger` | Cannot be undone: start a job, overwrite or delete files, bypass the checklist, change user libraries | **blocked**, every action needs confirmation in the program |

* `machine` and `danger` need **several approvals**: the option at start (`--allow-machine`, `--allow-danger`), the permission under *Extensions & AI*, and the **confirmation of every single action** in a dialog in the program. Esc declines; after 120 seconds the program declines by itself. Blocked tools do not even appear in the list.
* **Never:** writing controller settings (`$…=` and similar). This is not possible at any level, not even through the interface. Free-form lines to the controller are limited to simple, printable characters and one line, and commands that store something permanently in the controller are excluded. The checklist still blocks export and machine start when there are errors.
* **Scripts** never get more rights than the one who starts them.
* **The phone remote control** is never reachable for Claude, the interface or scripts.

### Uploading to the community portal: draft only

Claude can put a project in the [community portal](Community-Portal-en) as a **draft**. This is **off by default** and can only be switched on in the program (*Extensions & AI → Connect Claude → “Allow uploads to the portal (draft only)”*). Every upload first shows you a dialog with the exact content. Nothing is sent until you confirm. Only you can publish. The privacy check (file paths, user names) is mandatory. At most five requests per hour are possible. Claude never gets login credentials.

## The local interface (API)

With external control switched on, any program on the same computer can use the JSON interface, with the same levels and confirmations as Claude. It listens **only on `127.0.0.1`**, requires a random 256-bit access key (it is in the file `api.json` in the data folder, Windows: `%APPDATA%\ortino.CAM`), rejects requests from web pages in the browser and is **off by default**. Switching it off or closing the program removes the file immediately.

## The command line `ortino`

The command line generates G-code and checks projects without needing the program window. This is handy for series or automatic workflows.

| Command | Effect |
|---|---|
| `ortino gcode <projekt.ocam> [-o datei.nc] [--sheet ID] [--post ID]` | Generate G-code. Aborts on checklist errors. |
| `ortino check <projekt.ocam>` | Print the checklist (exit code 1 on errors) |
| `ortino info <projekt.ocam>` | Sheets, operations and time estimate |
| `ortino export <projekt.ocam> --format svg\|dxf [-o datei]` | Export the vectors of a sheet |
| `ortino demo -o beispiel.ocam` | Write the example project “Door sign” |
| `ortino posts` | List post-processors |
| `ortino ports` | List serial ports |
| `ortino series <vorlage.ocam> <daten.csv> --out <ordner>` | Batch production from a table (see [Sheets and furniture](Sheets-and-Furniture)) |
| `ortino script list`, `run`, `check` | List, run and check scripts |
| `ortino rpc <methode> [json]` | Call the JSON interface directly |
| `ortino package pack\|inspect …` | Design packages for the portal |
| `ortino --version` | Version |

```text
ortino check  tuerschild.ocam
ortino gcode  tuerschild.ocam -o tuerschild.nc --post grbl
ortino export tuerschild.ocam --format dxf -o tuerschild.dxf
```

The command line is a small program of its own (`ortino-cli.exe`, in the command `ortino`). It is **not** part of the installer. Whether it is available as a separate file for your version is stated in the notes of that version on the release page.

## Your own tools as scripts

With small scripts in the language **Rhai** (similar to JavaScript, built into the program, nothing to install) you build your own tools such as hole grids, sign frames or drilling patterns. You put a script file (`.rhai`) in the folder `scripts` in the data folder (*Extensions & AI → Scripts → Open folder*). Every script appears as a command in the command palette (`Ctrl+K`, “Script: …”) with an automatically generated input dialog, on the command line and as a tool for Claude. The result is **one** undo step, and if there is an error the project stays unchanged. Scripts run in a **sandbox** without file, network or process access, with a time limit (default 10 seconds). Scripts from community packages are never run.

## The assistant in the program

The built-in **assistant** is a sidebar (icon ✦ in the header bar or `Ctrl+L`) where you ask Claude questions, have messages from the checklist explained, and, if you wish, have projects set up. It needs **your own API key from Anthropic**. Without a key ortino.CAM works completely.

* **Privacy:** Before first use you confirm a notice about data transfer. **Nothing is sent before that.** What you ask and what Claude needs for the answer goes to the provider you have set (Anthropic by default). Images are only sent if you attach them yourself, with a preview before sending and an additional notice.
* **Key:** On Windows it is stored in the Windows Credential Manager, not in projects, settings or logs.
* **Costs:** Billing goes through your Anthropic account. The assistant shows the input and output amounts used, but deliberately no prices. You choose the model in the settings.
* **Undo:** All changes of one answer are a single undo step. The assistant has level `edit` at most. Machine and dangerous actions never belong to it.

## If it does not work

| Problem | Solution |
|---|---|
| Claude Desktop does not show ortino.CAM | Check the path in the configuration (doubled backslashes), quit Claude Desktop completely and restart it. |
| Changes do not appear in the window | `ortino-mcp` is working standalone. Switch on external control and restart Claude Desktop. You can check this with `ortino-mcp.exe --attach --check` in a terminal. |
| “Gesperrt: … braucht die Stufe machine” (“Blocked: … needs the level machine”) | Intended. If needed, put `--allow-machine` in `"args"` and allow machine commands in the program. Every action is confirmed. |
| “Keine Bestätigung … innerhalb von 120 s” (“No confirmation … within 120 s”) | The dialog in the program was not answered. |
| “… liest von außen nur Dateien aus freigegebenen Ordnern” (“… reads only files from allowed folders from outside”) | Intended. Put the file in `Documents\ortino.CAM` or allow the folder. Alternatively hand over text or upload in parts. |
| Windows SmartScreen or a virus scanner blocks `ortino-mcp.exe` | The file is not signed individually. If you trust the installer, allow the file once (see [Installation and updates](Installation-and-Updates)). |
| Installation or update reports that a file cannot be overwritten | The installer closes `ortino-mcp.exe` itself (not tested on Windows). If that does not help, quit Claude Desktop and restart the installation. |
