**English** | [Deutsch](Opferplatte-markieren)

# Marking the spoilboard

An assistant mills **marks into the machine’s spoilboard**: a zero cross and frame, a ruler with numbers, stop lines and a hole grid. With these you place workpieces accurately by eye and position clamps. The marks then also appear in the table view of the map in the “Cut” step.

> **Honest about the status:** All of this was **checked only against tests, the built-in machine simulator and Chromium**. **None of it was milled on a real machine.** How exactly the grooves sit depends on the repeatability of the homing switches, the runout of the bit and the condition of the spoilboard, and is not tested. The first time, **engrave shallow**, run the frame beforehand and look at the position on the table. Example values (for example 8 mm for holes) are examples, not manufacturer’s specifications.

> **This job mills into your machine’s spoilboard.** It must not be moved afterwards, and after surfacing the marks are gone.

## Opening

*Create ▸ Mark spoilboard …*, the command palette (`Ctrl+K`, “Mark spoilboard”) or the section “Marks” in the “Spoilboard” card in the “Cut” step. Beforehand, connect if possible and let it read the settings (that happens by itself on connecting).

## The four kinds

Each kind can be chosen separately and has its own values and depths.

| Kind | What |
|---|---|
| **Zero cross and frame** | cross at the home corner (or centre, or another corner), frame around the usable area, full line or corner marks only |
| **Ruler with scale** | ticks along the edges of the home corner (optionally on all four), numbers in single-line lettering, optionally continuous grid lines; division of 10/50/100 mm adjustable |
| **Stop lines** | corner square (an L with two legs) or stop edges at a corner, for placing a workpiece against or for screwing on a strip |
| **Hole grid** | holes in a grid for clamps or dowel pins (spacing, edge distance, diameter; the count and a preview are in the assistant) |

## Depths freely adjustable

* **Engraving depth:** one value for all lines and numbers (default shallow, 0.3 mm). Under “More settings” each kind has its own depth; the grid lines stay shallower.
* **Hole depth:** **“Spot only”** (default, 2 mm: mark the spot and drill by hand later with the matching drill), **“Drill deep”** (as deep as allowed), **“Like dowel pins”** (diameter and depth of the dowel pins from double-sided milling) or **“Custom”**.

## Protection against cutting through

Until now the program did not know the thickness of your spoilboard. The assistant **asks for it** (default 18 mm, **please measure**) and checks **every** depth against it: below the deepest point at least a **minimum rest** stays (default 3 mm, adjustable, never below 1 mm). Otherwise it is an **error with a suggested fix**, and “Create sheet” stays locked. The checklist and the **start check** (which blocks the start) then check the same limit.

## Findable again: referenced to the machine

The marks must be findable again later. That is why they refer to the machine’s **home position** (after homing), not to a freely set work zero. The assistant creates a sheet whose XY zero lies in the home corner; the start check **requires XY zero to be on the home position** and checks it. After homing, “Zero XY here” is enough. Without a known homing direction (`$23`) or home corner in the machine profile, the assistant does not plan, it does not guess.

**Z zero is the surface of the spoilboard:** probe on the spoilboard (touch plate) or set it by hand. With a fixed probe the start check offers the tool change “Pause” for this job; probe Z again on the spoilboard for each bit (first engraving, then drill).

## Procedure

1. Choose the **marks** and enter the spoilboard thickness, engraving depth and hole depth. In Easy mode only this is at the front, the rest is behind “More settings”. On the right the preview shows the table plan with travel, usable area, home corner and the planned marks.
2. **Check:** home corner, bit (suggestion or your own choice; V-bit or engraving bit for lines, drill or end mill for holes) and the checklist with fixes.
3. **Create sheet:** a normal sheet “Spoilboard marks” with locked layers and operations, engraving first, drilling last, in **one undo step**.
4. As usual **Check ▸ Cut**. The start check requires the confirmation “Cuts into the machine’s spoilboard”.
5. Afterwards, in the “Spoilboard” card, confirm **“Marks are milled”**. The program cannot know whether milling really happened; until you confirm, the marks appear as **“planned”** (dashed, faint) in the table view, afterwards as **“milled”** (strong). With “Not milled after all” and “Forget marks …” you take it back.

If the project already has the sheet, the assistant opens with its values; **“Recreate”** replaces the mark operations, your own shapes on the sheet stay.

## Limits

* There is **one** description of the marks per machine (it belongs to “My machine” and does not go into the shared package).
* The ruler’s numbers count from the frame corner in the home corner, not from XY zero.
* On the marking sheet the job’s toolpaths largely cover the lines; the holes stay visible.
* The “Like dowel pins” grid is only an auxiliary grid: the “Double-sided milling” assistant still drills its dowel holes itself for each workpiece.
* Not tested: repeatability of the homing switches, position and legibility of the grooves in MDF, Windows (WebView2).

## See also

* [Fixed probe and spoilboard](Fixed-Probe-and-Spoilboard)
* [Milling on the machine](Milling-on-the-Machine)
* [Double-sided milling](Double-Sided-Milling)

<!-- videos:start -->
## Videos (English)

* [![Plan marks for the spoilboard (video, English captions)](https://klapsc.github.io/ortino-cam/videos/spoilboard-marks-poster.jpg)](https://klapsc.github.io/ortino-cam/videos/#spoilboard-marks)  
**Plan marks for the spoilboard** · 14 s

All videos: [Videos](Videos-en).
<!-- videos:end -->
