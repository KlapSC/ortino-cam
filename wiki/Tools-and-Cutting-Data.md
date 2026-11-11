**English** | [Deutsch](Werkzeuge-und-Schnittdaten)

# Tools and cutting data

Which bit, how fast, how deep? This page explains the **cutter library**, the **guide values** for feed rate and spindle speed, the **proven cutting data** that you can save yourself, and the **tool life limits**.

> **Honest about the status:** All cutting values in the program are **guide values**. They are calculated from material, bit diameter, number of flutes and the limits of your machine and are **not measured on a real machine**. They depend on your machine, your bit and your material. Check them, start carefully and try on an offcut. The catalogue dimensions of the bits do not come from data sheets (see below). Tool life limits and maintenance intervals are **only checked against the simulator** and are not a manufacturer’s specification.

## Tools in the project

Every project has its own **tool list**. Every operation uses a tool from it. A tool has a type (end mill, ball nose bit, V-bit, drill, engraving bit, thread mill …), dimensions, number of flutes and guide values for spindle speed, feed rate, plunge feed rate, depth per pass and stepover. You manage them in the tool dialog (“Manage tools”). The program knows standard tools: end mills from 3.175 to 6.35 mm, a ball nose bit, V-bits, a 3 mm drill, an engraving bit and a thread mill. If one of them is missing, the assistants (for example quick start) add it to the project when needed.

## The cutter library

The library contains over 250 bits from eleven manufacturers (among others Amana, SpeTool, Whiteside, Onsrud, Yonico, IDC Woodcraft, Bits & Bits, Sienci Labs, Inventables, Carbide 3D, Genmitsu). You can open it through the command palette (`Ctrl+K`: “Open cutter library …”), the tool dialog or the bit choice of an operation (“Choose from the cutter library …”).

**Searching:** The search field forgives typing errors and reads dimensions: `6mm`, `1/4`, `0.25in`, `60°`. Examples: “compresion 6mm”, “60° v”, “ball 1/8”. There are filters for manufacturer, type, cutting direction, diameter, flute length, shank, number of flutes, angle, material and more. The quick filter **“for board ≥ thickness + 0.3”** shows only bits that are long enough to cut through. You can compare two or three bits and mark favourites.

**Selection helper:** You state the task (contour, pocket, V-carving, engraving, inlay, surfacing, drilling, 3D relief, chamfer), material, sheet thickness and smallest detail, and the program suggests bits, each **with a reason**. These are rules of thumb, not a guarantee. For example, the flute must be longer than depth plus 0.3 mm when cutting through, so for 18 mm birch plywood at least 18.3 mm. The diameter must never be larger than the smallest detail. For plywood, melamine and hardwood a compression bit is more likely to fit, for plastic and aluminium a single-flute bit, for fine text a 60° V-bit. If nothing fits, the program says why and what you can relax.

### How reliable are the catalogue data?

The catalogue entries come from **search result texts** of the manufacturers’ and dealers’ pages (as of October 2026). The original pages and data sheets could not be retrieved, and nobody has measured the bits.

| Label | Meaning |
|---|---|
| **Verified** | The dimensions were stated explicitly in the text of the source and are plausible. It does **not** mean that anybody measured them. |
| **Derived** | From a series table or calculated (for example the flute length of a V-bit from diameter and angle). |
| **Unverified** | The source was contradictory or incomplete. The reason is in the note. |
| **Own** | Your own entry. |

**Check the dimensions with the manufacturer before you buy.** Every entry has a source link (“Copy link”). There are no prices. Missing, for example, are metric 6 mm long-flute bits and some brands for which nothing reliable could be found (QWOCA, Drillman, Vortex, Stepcraft, Sorotec, CNC-Step, Onefinity). Manufacturers’ chip-load tables are **not** included.

### Your own bits

Under **My library** you enter the bits you actually have: type, diameter and flute length are required, everything else is optional. Missing details are estimated by the program and reported (“please measure”). You can edit, duplicate and delete entries. With **Back up (export JSON)** and **Restore (import)** you take your library to another PC. Existing bits are never overwritten in the process. The library is the file `tools.json` in the data folder (under Windows `%APPDATA%\ortino.CAM`).

### Import and export

You can read in bit lists from other programs: **Vectric** (`.vtdb`), **Fusion 360** (`.json`, `.tools`), **CSV** (column mapping can be changed in the preview), **LinuxCNC** (`.tbl`) and the program’s own JSON export. Before applying, you see a preview (new, duplicate, error). Nothing is ever overwritten. You can export as CSV, JSON or Fusion 360 JSON.

> **Limits:** The `.vtdb` format is not officially documented and was **not tested with a real Vectric file**. The Fusion format has not been checked with real files either, and the Fusion export was not loaded into Fusion.

## Guide values for feed rate and spindle speed

When you choose a tool, the program shows cutting values as a suggestion: spindle speed, feed rate, plunge feed rate, depth per pass and stepover. They are formed like this:

* a base value from material, diameter and number of flutes,
* factors for the **material group** (softwood, hardwood, plywood, MDF, acrylic, plastic, rigid foam, aluminium) and the **wood species** (29 wood species, boards and plastics with a hardness class),
* factors for the **bit type** (for example down-cut spiral or roughing bit),
* **chip thinning:** with a narrow side engagement the feed rate is raised so that the chip does not get too thin (at most to double),
* limiting to the limits of your machine (maximum feed rate, spindle speed range, 80 % of the spindle power, if known).

**“Why this feed rate?”** shows you every step with factor and value. In Easy mode there is a clear line such as “Cutting values from the bit: 2880 mm/min at 18000 rpm”. The factors of the material database are **assumptions** (classification by hardness and usual workshop practice), not measured. Hardness values shown in the program are for display only. The program’s notes warn if a feed rate is far above the guide value (“Feed far above the guide value”), the chip gets too thin (“Chip too thin – burn risk”) or the depth per pass is too deep.

## My proven cutting data

If a project went well, you can remember the values of that operation as **proven**: feed rate, spindle speed, plunge feed rate, depth per pass and stepover. Future suggestions and new operations then prefer them, with the origin (“proven, confirmed 3 times, last on …”). The guide value stays next to it for comparison.

* An entry applies to **tool + material (+ operation type)**. The same tool in another project is recognised.
* Saving: in the operation’s properties panel (section “Feed & speed”) click **“Save as proven”**, or after a run via the note “Did it run well? Save the cutting data as proven”.
* View, edit, delete: tool dialog → **“My cutting data”**.
* **Machine limits always apply:** Proven values are capped to the limits of the project’s machine, and the program reports it.
* The program **learns nothing by itself**. An entry only comes into being when you save it. The values are your experience on **your** machine with your material and are not checked and not transmitted anywhere. The material match is exact: an entry for `plywood` does not apply to `birch_plywood`.

## Tool life limits and maintenance plan

The **job log** records what you actually milled: one entry per program run with estimated and actual time (without pauses and waiting time during tool changes), result and tools. It is stored only locally on your computer, never contains G-code or paths and never leaves the computer. Running the frame and probing are not logged. From it come:

* **Time calibration:** After at least three completed runs of at least five minutes each, the start dialog shows “Based on your previous runs about …”. In the setup sheet you can calibrate the time estimate with it (off by default, see [Setup sheet and quote](Setup-Sheet-and-Quote)). The factor is a median over a few runs, not a promise.
* **Tool life limit per tool:** In the tool dialog you enter a limit in **minutes of cutting time**. The program counts the cutting time since the last reset. The start check points it out from 80 % of the limit and warns if the run would exceed the limit. After changing a bit or sharpening it, you click “Reset tool life”. There are no material factors: anyone who mills hard materials sets the limit lower. Air cuts do not count.
* **Maintenance plan per machine:** In the job log there is the **“Maintenance”** tab. Items such as spindle, lubrication, spoilboard or filter get an interval in operating hours, calendar days or runs. The start check reports due items (a note from 90 % of the interval, a warning when overdue). With “Done” you reset the counter.

The time per tool is an approximation (it follows the line last confirmed by the controller and can deviate by a few seconds at tool changes). Limits and intervals are **guide values without measurement and without a manufacturer’s specification**.

<!-- videos:start -->
## Videos (English)

* [![Pick a cutter from the library (video, English captions)](https://klapsc.github.io/ortino-cam/videos/tool-library-poster.jpg)](https://klapsc.github.io/ortino-cam/videos/#tool-library)  
**Pick a cutter from the library** · 13 s

All videos: [Videos](Videos-en).
<!-- videos:end -->

## Next

* [Operations](Operations)
* [Checking and simulation](Checking-and-Simulation)
* [Setup sheet and quote](Setup-Sheet-and-Quote)
