**English** | [Deutsch](Doppelseitig-fraesen)

# Double-sided milling

Some workpieces need machining from **both sides**: a pocket on top and a chamfer underneath, a handle that is routed out from behind, a sign engraved on front and back. ortino.CAM helps with **two dowel pins**: side A drills two holes through the workpiece into the spoilboard, you put pins into them, flip the workpiece, push it onto the pins, and side B lies exactly where it belongs.

> **Honest about the status:** Double-sided milling has **only been checked against the simulator, automatic tests and in the browser (Chromium), never on a real machine**, and not systematically on Windows (WebView2). How exactly side B fits side A depends on your pins, the drill bit and the spoilboard, and that is **not tested**. The first time, try it on an offcut, use pins with little play and run the frame before side B.

## How it works

* **Side B is a sheet of its own** with the same width, height, thickness, the same material and the same work zero as side A. You draw it **as it looks from above after flipping**.
* The G-code of both sides is entirely ordinary G-code. **Nothing is mirrored on export.** Mirroring happens only in the drawing aids.
* The two **dowel holes** are mirror images of each other about the **flip axis**. After flipping, they are therefore at the same places on the sheet again. On side A they are drilled; on side B they are only drawn as a mark.

| Flip axis | How you flip | A point at the bottom left of side A ends up |
|---|---|---|
| **Vertical** (default) | about the vertical centre line, swapping left and right, like turning the page of a book | at the bottom right |
| **Horizontal** | about the horizontal centre line, swapping top and bottom, like flipping a calendar page | at the top left |

## What you need

* Two **dowel pins** (for example wooden dowels or steel pins) with the diameter of the bit that drills the holes. A tool close to 6 mm is suggested.
* A **spoilboard** into which the holes may go a few millimetres deep (default 4 mm). ortino.CAM does not know its thickness. Check yourself that it is considerably thicker.
* **Waste at the edge:** The holes need room outside your parts, default 12 mm from the edge to the hole centre.
* Preferably **Z zero on the table** (the spoilboard). Then one work zero applies to both sides. With Z zero on the top you have to probe again after flipping.

## Step by step

1. **Draw side A** and create its operations. Leave a gap to the edge of the sheet.
2. Menu **Create → “Two-sided machining …”** (or command palette `Ctrl+K`, “two-sided”). The assistant has three steps:
   * **Flip axis:** vertical or horizontal, with a sketch.
   * **Dowel pins:** tool, position of the holes (“On the flip axis” or “At the edges”), edge distance, depth into the spoilboard and an **offset against flipping the wrong way**. On the right you see the sheet with the holes and below it the check messages, each with a solution. A hole that is too close to a part is red.
   * **At the machine:** positions of the pins relative to the XY zero, drilling depth, the names of the G-code files and numbered instructions.
3. **Apply.** The sheet is now called “Side A”, and “Side B” is created behind it. Both sides get the locked layer “Dowel pins” with the marks. Side A gets the drilling “Drill dowel holes” as its **first** operation. This is a single undo step.
4. **Draw side B.** At the top right of the drawing area there is a bar with:
   * **“Other side”:** The other side shows through as dashed lines, already mirrored. This way you see where the parts of side A will be after flipping.
   * **“Copy mirrored”:** The selection (for example the outer contour) is copied mirrored to the other side. Also in the context menu under “Mirror”.
   * **“To side A/B”** and the settings.
5. **Check.** The checklist reports when something about the coupling is wrong (see below).
6. **Mill side A.** The start check reminds you that the dowel holes are drilled first. Do not put any clamps over the holes.
7. **Flip:** Release the workpiece, blow the chips out of the holes, put the pins into the holes in the spoilboard, flip the workpiece about the flip axis, push it onto the pins and clamp it. Do **not** change the XY zero.
8. **Mill side B.** The start check asks **“Workpiece flipped and pushed onto the dowel pins?”**, which you have to confirm. It also tells you whether a complete run of side A is in the job log, and whether Z zero still applies.

**Changing:** The assistant opens with the previous values. **Removing:** “Create → Remove two-sided setup …” removes the coupling, marks and drilling; side B stays as a sheet of its own. If you delete one of the two sides, the coupling is removed as well. The program says so beforehand, and “Undo” restores everything.

## What stays together

* If you change width, height, thickness, material or work zero on one side, the other side takes over the value.
* The drilling depth is **thickness plus allowance**. If you change the thickness, the depth follows.
* The holes and marks are recalculated after every change.
* The **sheet planner** does not place any parts over the holes or close beside them. It does move the parts of one side without taking the other side along. Check afterwards with “Other side”.
* **Templates and series:** A series as individual files produces the G-code files of both sides for each row. In sheet mode a two-sided template cannot be arranged; the program says so, with a solution.

## What the checklist reports

| Message | What to do |
|---|---|
| Side A and B differ in size, thickness, material or work zero | adjust one side to the other, then they follow each other again |
| Z zero is “Top of sheet” | better choose Z zero “Table (spoilboard)”, otherwise probe again on side B |
| Tool is missing or unsuitable (V-bit, thread mill) | choose a drill or end mill with the diameter of the pins |
| A hole is not entirely on the sheet or too close to a part (side A or B) | change the edge distance, choose the other position or place the parts further from the edge |
| The drilling is missing, switched off or not the first operation | if it is missing, “Apply changes” in the assistant creates it again; otherwise switch it on or move it up in the list of operations |
| “Does not drill through”: depth less than thickness plus 2 mm | increase the depth into the spoilboard |
| Both sides have the same name | rename one side, otherwise the G-code files would get the same name |
| Note about the spoilboard | pin diameter and length are given; the pins must not stand above the top surface |

## Setup sheet and G-code

* Each side gets its own G-code file, for example `Kiste_Seite_A.nc` and `Kiste_Seite_B.nc`.
* The [setup sheet](Setup-Sheet-and-Quote) of each side has a section “Two-sided: side A → flip → side B” with flip axis, pins, pin positions, drilling depth and the steps at the machine. On side B there is an additional checkbox “Side A is done; workpiece flipped”.

## Flipping against a stop edge (since 0.6.0)

Instead of two dowel pins, you place the workpiece for **both** sides in a **stop corner** on the spoilboard: a straight **rail** along one edge and an **end stop** on the adjacent edge. After side A the workpiece is flipped along the rail and placed in the corner again. In the assistant you choose “Locating after flipping: **Stop (edge)**” at the top of the second step and the corner; the preview shows the rail, the end stop and the corner of side A that ends up there on side B.

* **Size in flip direction:** At the end stop, side B sits shifted in flip direction by the deviation of the real workpiece size (never with pins). The size must therefore be right; the checklist reminds you.
* **Checklist:** Is the stop present and square? Is the contact exact? Work zero at the stop corner? Toolpaths beyond the rail or end stop (an error if they cut almost all the way through there)? The program does not know the height of the rail.
* **Instructions at the machine, start check, setup sheet and sheet planner** know this variant (the sheet planner reserves a strip 3 mm wide inside along the rail and end stop). Tip: With “Mark spoilboard → Stop lines” you mark out the rail.
* Old files load unchanged. Older program versions read a stop file only as an incomplete dowel-pin coupling and show errors in the checklist.
* None of this has been checked on a real machine.

## Limits

* Since 0.6.0 the **simulation** calculates both sides together: side B starts from the material state after side A (mirrored at the flip axis), breakthroughs and dowel holes appear in the picture, and a warning appears if less than 1 mm remains between the two sides or a toolpath of side B reaches into a dowel pin. The switch **“Side B only”** calculates as before from the full block. The simulation is accurate to one grid cell, assumes milling from above and simulates neither flipping errors nor the play of the pins.
* With pins there are always **two pins**; a fitting shape in the spoilboard does not exist. Instead of the pins there is, since 0.6.0, **flipping against a stop edge** (above).
* Without an **offset** the workpiece also fits onto the pins when flipped wrongly (turned by 180°). An offset of a few millimetres prevents that.
* **Copy mirrored** also mirrors text (mirror writing). For lettering on side B, better write it anew.
* The job log recognises side A by the project and sheet name. After renaming or when a run happened on another computer, the warning to confirm remains.
* The checklist reports in German; the assistant shows the same messages in English too.

<!-- videos:start -->
## Videos (English)

* [![Machine both sides with dowel pins (video, English captions)](https://klapsc.github.io/ortino-cam/videos/double-sided-poster.jpg)](https://klapsc.github.io/ortino-cam/videos/#double-sided)  
**Machine both sides with dowel pins** · 18 s

All videos: [Videos](Videos-en).
<!-- videos:end -->
