**English** | [Deutsch](Moebel-Designer)

# Furniture Designer (tables, sideboards, shelves, seating)

Besides the kitchen you design **furniture** in the same dialog: tables, sideboards, shelves and seating. Materials, edge banding, colours, handles, reliefs, parts list, nesting, setup sheet and quote, “Create parts & prepare milling” and undo work as for the kitchen (see [Sheets and Furniture](Sheets-and-Furniture)).

> **Honest about the status:** Everything here is **calculations and common workshop dimensions**, checked only against tests, simulator and Chromium. **None of it has been milled, built or loaded.** The checks (tipping, deflection, webs, inside radii) are **hints from simple formulas, not a strength verification**; material properties, loads, test loads, plug-in clearance and weights are **assumptions**, which are stated in every message. **Before any series, build a test piece from the real material and test it with the intended load.** For chair, stool and bench this is a requirement.

> **Also in the browser:** Since 0.5.0 this designer is also available in the community portal (without the program, without milling): [Web Designer in the Portal](Web-Designer-in-the-Portal).

## Opening

In the furniture designer (`Ctrl+Shift+M`) use the **Kitchen | Furniture** switch at the top, or in the command palette (`Ctrl+K`) “Furniture designer: open the Furniture area”, “Furniture: create a dining group” or “Add furniture: …”. Kitchen cabinets and furniture pieces can be in the same project; each area shows only its own pieces, the parts list, nesting and “Create parts” contain both.

On the left is the list, grouped by tables, sideboards, shelves and seating, with the *Piece* button; a dot on an entry shows a warning or an error. In the middle is the 3D preview and below it the **floor plan**, on the right the fields of the selected piece. All lengths take a number or a formula with project variables. In **Easy mode** the fine points of the construction are behind *More settings*.

## Types of furniture

Default size width × height × depth in mm.

| Type | Default | Choices |
|---|---|---|
| **Dining table** | 1800 × 740 × 900 | Top rectangular, soft rectangle, stadium, oval, round; edge straight, chamfer (90° bit) or radius (hand work only); base apron frame with four legs, plate feet, cross base, A-frame; top split into 2–3 parts |
| **Coffee table** | 900 × 380 × 600 | like the dining table |
| **Side table** | 450 × 550 × 450 | like the dining table |
| **Nesting tables** | 700 × 500 × 460 | 2–3 tables that fit into each other, with clearance check |
| **Sideboard / lowboard / TV board** | 1800 × 650 × 420 | Plinth, legs or sled base; doors, drawers, flaps, open bays; shared dividing walls, grooved back panel, cable opening |
| **Bookcase** | 800 × 1800 × 320 | Shelves on System 32, fixed in grooves or plugged in; load assumption per metre of shelf |
| **Ladder shelf** | 700 × 1800 × 450 | two slanted stiles, plugged-in shelves, leans against the wall |
| **Modular shelf** | 1200 × 1200 × 340 | Grid of columns and rows |
| **Wall shelf** | 800 × 240 × 230 | Box or board; wall fixing as a bought part with a note |
| **Stool**, **panel stool** | 360 × 450 × 360, 380 × 450 × 320 | Seat on apron frame, plate feet or cross base, or on two side panels respectively |
| **Bench** | 1400 × 450 × 380 | Top on plate feet, apron frame, cross base or A-frame |
| **Plywood chair** | 440 × 840 × 520 | two profiled side panels, slanted seat and backrest, cross brace |
| **Chest of drawers**, **highboard** | (since 0.4.1) | Drawer carcass with drawer boxes on full-extension runners (13 mm side clearance), plinth, legs or sled base, back panel; bays suggested according to the width |
| **Nightstand** | (since 0.4.1) | Bay with drawer, also drawer above an open bay; height relative to the mattress as a guide value |
| **Desk** | (since 0.4.1) | Side panels with modesty panel, apron frame, plate feet or sled base; optional drawer unit left or right and cable opening (round or slot) |
| **Coat rack** | (since 0.4.1) | Wall panel with hook rail and shelf on plugged-in brackets; hooks and wall fixing are in the parts list |
| **Shoe bench / shoe cabinet** | (since 0.4.1) | up to 480 mm in height a bench with open bays, above that a cabinet |

Since 0.6.0 there are two more kinds of seating:

| Type | Construction |
|---|---|
| **Lounge chair** | two large side panels as contour plates (feet with arch, seat line, tilted backrest), seat and backrest board, selectable cross braces, optionally an armrest as part of the side panel (passes through a slot in the backrest board). No upholstery: **a cushion appears only as a bought part with guide dimensions in the parts list**. |
| **Swivel chair** | **Seat and backrest** made of sheet; **five-star base, gas lift, casters, seat plate and back bracket are bought parts** (in 3D as simple placeholders, listed in the parts list). Holes for M8 threaded inserts on the underside of the seat and the back of the backrest. |

The five new bought parts of the fittings library are **generic** (without manufacturer, link or price, marked “unverified – check on the real part”); the drilling patterns are assumptions, **check them on the real five-star base before you drill**. The checks (seat height, depth, backrest tilt, tipping backwards and forwards, five-star base diameter, gas lift stroke, deflection of the seat board) are hints from simple formulas, **not a strength verification**; EN 1335 and EN 16139 have not been checked. None of it has been milled, built or loaded. Upholstered furniture, beds, rocking mechanisms and armrests on the swivel chair still do not exist.

## Joints

* **Glueless plug-in:** tenons through slots. The clearance comes from the fit assistant (project variable `Spiel`), otherwise the program assumes 0.15 mm. The slot corners get **dogbones** to suit the bit. **Tenon and slot are created from one description** and therefore always fit together in the calculation.
* **Classic:** tenons in blind mortises (glued), dowels or confirmat screws (as a bought part in the parts list).
* With the **sideboard** only the base is glueless plug-in; the carcass stays with the connectors of the kitchen modular system.
* **Finger joints** (since 0.4.1) sit at the outer corners of the carcass and at the drawer box corners, only in plywood and solid wood; with coated board, chipboard or OSB the classic joint stays, with a warning. Dovetail and mitre are not connected, and fingers only at the outer corners, not at inner joints.

## Style templates

Six templates set material, thicknesses, colour, gloss, handle, shapes and joint in one step, after which everything can be changed freely: **Soft modern**, **Japandi**, **Fluted**, **Sculptural**, **Warm minimal** and **Dark**. They are general names without manufacturer and without copies of protected furniture, and they are **assessments of current directions, not market data**. In the painted templates tables, seats and shelves take plywood instead of MDF, because MDF gives way under permanent load.

## Dining group and layout

*Create dining group* asks for the number of people (2–10), table shape, style and, if you want, chairs at the ends and a sideboard; the program calculates table size and chair places (60 cm per place), and everything is created in **one** undo step.

In the floor plan pieces can be **dragged** (grid 10 mm, 100 mm with `Shift`) or set via the fields *Position x*, *Position z* and *Rotation*. This is **not a room planner**: no walls, doors, windows or sockets. There is only a warning when pieces overlap in the floor plan (a chair that fits under the table top is only a hint).

## Checks

Every message states the assumption, the calculation and a **suggested solution**:

* **Ergonomics:** common ranges for table height, seat height and depth, legroom, places per person.
* **Tipping:** load at the edge of the top (tables with 15 or 40 kg, seats with 80 kg assumed), chair backwards, shelves and wall (with a note on the wall fixing).
* **Deflection:** beam formula, note from L/300, warning from L/200, with load assumptions for shelves (default 40 kg per metre), table top and seat.
* **Webs and bit:** web width, slot width and inside radii against the bit of the machine.
* **Travel:** if a part does not fit into the travel, the list names solutions (split, scale, another sheet or machine, several set-ups).
* **Test piece:** always for chair, stool, panel stool and bench.
* **New in 0.4.1:** **anti-tip fixing** for chest of drawers and highboard (wall fixing as a mandatory note) and **tipping with a drawer pulled out**; drawers (extension, load, width, stop, bottom); desk (height, depth, legroom, cable opening); nightstand against the mattress height; coat rack (load per wall screw, hook spacing); shoe bench as a seat; **racking** when there is no back panel; fingers (bit, width, material). The loads (for example 30 kg per pair of runners, 20 kg extra load when tipping) are **assumptions**, racking is a rule of thumb.

The calculations assume a freely supported beam and rigid joints; joints, fittings, glue lines and the load transfer in the legs are **not verified**. Weights are rough (volume times bulk density, without fittings and glue).

## Nesting: “Optimised” and saw plan (since 0.15.0)

In the **Nesting** view (key `3`) there are three methods: **MaxRects** (tightest packing for the CNC), **Guillotine** (through cuts, saw friendly) and, since 0.15.0, **Optimised**.

* The **“Optimise cutting”** button sets the method **Optimised**, recalculates the nesting and reports before and after: fewer sheets (with utilisation), a larger offcut on the last sheet or “No better layout found”. It **stays in the designer**; up to 0.14.0 it opened the sheet cutting dialog instead, whose result did not come back into the nesting view.
* **Optimised** tries MaxRects and Guillotine with the fixed sort orders and 48 perturbed orders each and takes the layout with the fewest sheets, in a tie the one with the emptier last sheet (the larger offcut). Same input, same result. **“Create parts & prepare milling”** uses the same layout.
* **Measured** on 30 random cases on the computer: never worse than the fixed methods, once one sheet fewer, 15 times an emptier last sheet. **The gain is mostly small**, and it applies to made-up cases, not to your parts.
* **Optimised is not the saw plan.** It takes the layout with the fewest sheets, even if it comes from the MaxRects method and cannot be sawn with through cuts. For the panel saw you choose **Guillotine** or open the **saw plan**: that is the **“Saw plan …”** button (formerly “Optimise cutting …”), it opens [Sheet Cutting](Sheet-Cutting) with the dimensions from the parts list and leads back into the designer when you close it (same view, same selection). There is no saw plan button in the web designer of the portal.
* **Caution with files:** A file in which the method **Optimised** is selected cannot be opened in older program versions (up to 0.14.0). A single click on “Optimise cutting” sets it in the project; if you want to pass the file on, choose MaxRects or Guillotine first.
* **Calculated only:** never tried on a real saw or CNC router, not checked under Windows (WebView2).

## Rendering

*Rendering* in the Furniture area shows a **furniture scene** with floor (parquet), wall behind the rearmost wall piece, side walls, a selectable rug and wood grain along the fibre. As with the [Kitchen Rendering](Kitchen-Rendering): a quick WebGL image, **not a photorealistic render**, checked only in Chromium with software graphics, screen colours are not colour samples.

## Keyboard

`↑`/`↓` select the next piece, `N` creates a new piece of the selected type, `Del` deletes, `K` shows the overview, `R` opens the rendering, `Ctrl+Z`/`Ctrl+Y` undo and redo. Moving is done by dragging (mouse, finger, pen) or via the fields, not with the arrow keys.

## Limits

* Radius and chamfer edges cannot be seen in 3D; the radius is hand work.
* No room planner, no check against the kitchen, no automatic arranging.
* The rendering has never run under Windows (WebView2) or on a real graphics card.
* The **Optimised** nesting (since 0.15.0) has only been measured on the computer, not sawn (see above).

## See also

* [Sheets and Furniture](Sheets-and-Furniture) (kitchen, sheet planner, fits)
* [Kitchen Rendering](Kitchen-Rendering)
* [Setup Sheet and Quote](Setup-Sheet-and-Quote)

<!-- videos:start -->
## Videos

* [![Design furniture: tables, shelves, chairs (video, English captions)](https://klapsc.github.io/ortino-cam/videos/furniture-designer-poster.jpg)](https://klapsc.github.io/ortino-cam/videos/#furniture-designer)  
**Design furniture: tables, shelves, chairs** · 14 s

All videos: [Videos](Videos-en).
<!-- videos:end -->
