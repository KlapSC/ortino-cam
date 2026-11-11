**English** | [Deutsch](Fester-Taster-und-Opferplatte)

# Fixed probe and spoilboard

This page belongs to [Milling on the machine](Milling-on-the-Machine). It explains two aids for machines with a permanently installed tool probe: The **fixed probe** measures the length of every clamped bit. The **height map** compensates for the unevenness of the spoilboard.

> **Honest about the status:** According to feedback from the operator (Ultimate Bee with xPRO V5, version 0.3.10), **setting up the fixed probe and measuring a tool** work on a real machine. **Only checked against the simulator and automatic tests** are the tool change at the fixed probe in the middle of the program and the measurement of the spoilboard with a height map, never with a real spoilboard. The wiring notes come from the operator (Ultimate Bee with xPRO V5) and have not been verified on the hardware. Read the manual of your controller before connecting. First measurement without material, hand on the emergency stop.

If your setup is simpler (touch plate, tool change with a pause), you do not need this page.

## Terms

* **Spoilboard:** the board on the machine table that the bit may cut into when cutting through. It protects the table.
* **Z zero on “Table (spoilboard)”:** All depths in the project count from the surface of the spoilboard. The workpiece on top is then exactly as high as its thickness. You can set this in the project (step “Project”, sheet settings).
* **Fixed probe:** a mechanical probe that sits permanently in the machine. When the tip of the bit touches it, it triggers.
* **Height map:** a measurement of the board height at a grid of points.

## Fixed probe

### How it works

The probe triggers when the tip of the bit rests on its trigger surface. This surface is at a fixed height above the spoilboard. Whichever bit triggers it, its tip is exactly there. The program sets Z zero accordingly, **without knowing the length of the bit**. A longer bit triggers earlier and gets a different offset.

You determine the height of the trigger surface **once** with a **reference bit**: zero the spoilboard (tip on the surface, for example with a sheet of paper), then trigger the probe with the tip. **Spoilboard and probe must be measured with the same bit.** The program remembers the name of the reference bit and warns if the names differ.

### Choosing the probe

* A mechanically switching probe with a **potential-free contact** (normally closed or normally open).
* **No current through the bit.** A probe that puts the bit under voltage can damage the spindle and electronics.
* The spread of two measuring passes may be at most **0.5 mm**, otherwise the measurement is aborted. For clean results it should be well below that.
* Mounted firmly and free of chips, with room to approach from above, cable not in the way of the bit.

For the xPRO V5, according to the operator (not verified): The probe connector is a three-pin plug. **SIG** and **GND** are used, the middle pin stays free. If the probe switches “the wrong way round”, a controller setting (`$6` for GRBL, `$Probe/Invert` for FluidNC) reverses the logic. ortino.CAM shows you the line to copy, but never sends it.

### Setting up (once per machine)

In the **Fixed probe** card in the step “Cut”:

1. **Requirements:** connected, homing done, idle, probe input open. With **“Test probe input”** you check that the input switches on contact and falls back on release. Clamp the reference bit, spindle off.
2. **Position:** With jogging, move the bit over the **centre of the trigger surface** and “Save X/Y here”. The **approach height** is the height at which the machine later travels to the probe in X/Y. It must be above clamps and workpiece. Choose the **search path** (default 40 mm) generously, because shorter tools trigger lower.
3. **Measuring:** The machine travels over the probe, probes quickly (200 mm/min), retracts 2 mm and probes precisely (40 mm/min).
4. **Height of the trigger surface** above the spoilboard: from the saved Z zero of the spoilboard, from the current Z zero of the controller, or entered by hand.
5. **Saving:** The result is stored in the machine profile (for your own machines also in the machine list).

### For every job

1. Homing.
2. Clamp the bit and click **“Measure tool”**. The machine measures and puts Z zero on the spoilboard.
3. Set the X/Y work zero on the workpiece by hand.
4. In the project, set Z zero to **“Table (spoilboard)”**. From version 0.3.11, with a fixed probe set up, this is the default for new projects (changeable in the menu “Settings” ▸ “Machine & Z zero …”); you switch an older project with the button **“Set to spoilboard”** in the card. If it is set to “Top of sheet”, the card warns and asks twice, because otherwise the program would cut too deep by the material thickness.
5. Start check, run. With a fixed probe set up, from version 0.3.12 the program changes **by itself at the probe** (tool change “Automatic”); the start check says what applies. If you prefer to change with a pause, click **“Use pause instead”**. A choice you saved explicitly stays as it was.

A tool change in the program works like this: stop, move to the approach height, you change the tool and press “Continue”, the machine measures the new tool, sets Z zero and returns to the old position. Afterwards both tools stand at the same height above the spoilboard at the same workpiece Z (checked in the simulator with bits of different lengths).

After a run with a tool change, Z zero belongs to the **last measured** tool. If the next run starts with T1 again, you clamp T1 and click **“Measure tool”** once more – the start check blocks until then (“Z zero belongs to another tool”). *Simulator only.*

### Safety

* Only after homing. If the probe input is already triggered, the program sends nothing.
* In X/Y the machine travels **only at the approach height**, never diagonally.
* The program **never switches on** the spindle during this and does not check whether it is running. Switch it off by hand before measuring.
* You can stop at any time. Z zero is never set halfway: It only exists once both measuring passes were valid.
* If the probe finds no contact within the search path, the alarm stays. The message gives the solution (unlock, check position and cable, measure again).

After a knock or a rebuild you must set the probe up again. The spread check catches gross errors, not a displacement of the probe.

## Zeroing the spoilboard and height map

A spoilboard is never completely flat and warps with moisture. A height map measures the unevenness **once**, stores it in the machine profile and compensates for it when milling: The tip of the bit follows the board.

| Important | Hardly needed |
|---|---|
| Engravings and shallow depths (0.1 to 1 mm) | Pockets and contours that cut deep enough |
| V-carving and inlays (the depth determines the line width) | Through-cuts where the spoilboard is cut into anyway |
| Large workpieces where the board varies by tenths of a millimetre | Small parts on a resurfaced board |

### Operation

Step **Cut**, card **Spoilboard**. Requirements: connected, homing, probe input open, board clear.

1. **Zero:** The current X/Y position is the reference point. Either *probing with the touch plate* or *by hand* (tip on the surface, paper in between, its thickness is subtracted). Enter the **reference bit**. A new zeroing discards the old height map.
2. **Choose the grid:** Area and spacing (default 50 mm, 25 mm for strong waviness). The program shows the number of points and the estimated time. At most 40,000 points.
3. **Measure:** For each point the machine travels to safe height, probes quickly, retracts and probes slowly. Progress and cancelling are possible at any time.
4. **Result:** A colour map (blue low, orange high) shows range and spread. “Save” stores the height map.

The start dialog then shows the switch **“Apply the spoilboard height map”**.

### How the compensation works

* The **exported G-code stays unchanged**. Only the lines that go to the controller are converted at the start.
* Moves that run entirely above the top of the material plus the highest elevation (plus 1 mm) stay unchanged.
* All others are split into short pieces so that the tip follows the board.
* **Arcs become straight lines**, because an arc cannot follow an inclined surface. The chords deviate from the arc by at most 5 µm. This means more lines and a slightly higher data rate.

### Limits

* Applies only to projects with Z zero on **“Table (spoilboard)”**.
* The workpiece must lie flat on the board. **Warping of the workpiece itself is not captured by the height map**; it measures the board.
* The program must lie **entirely within the measured area**, otherwise the start is rejected.
* After 180 days the start check warns that the measurement is very old. After surfacing, replacing or moving the board it is invalid. Mark it as outdated and measure again.
* Measure again: after changes to the table or the Z axis, after changing the probe or the probing feed rate, and for engravings after large swings in humidity or temperature. A spot check with paper at two or three places helps.
* Real firmware, real probes and real boards are **not checked**. Neither is the behaviour of the planner with very many short lines.

## More

* Surfacing the spoilboard (the operation “Surfacing”) is described on the page [Operations](Operations).
* Milling marks (cross, frame, ruler, stop lines, hole grid) into the spoilboard: [Marking the spoilboard](Marking-the-Spoilboard) (since 0.4.1; the table view of the card in the step “Cut” shows them as planned or milled).
* Back to [Milling on the machine](Milling-on-the-Machine).

<!-- videos:start -->
## Videos (English)

* [![Plan marks for the spoilboard (video, English captions)](https://klapsc.github.io/ortino-cam/videos/spoilboard-marks-poster.jpg)](https://klapsc.github.io/ortino-cam/videos/#spoilboard-marks)  
**Plan marks for the spoilboard** · 14 s

All videos: [Videos](Videos-en).
<!-- videos:end -->
