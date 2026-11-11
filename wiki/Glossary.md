**English** | [Deutsch](Glossar)

# Glossary

Short explanations of the terms used in ortino.CAM and in this wiki. Sorted alphabetically by the English term; the German term is given in brackets where it differs.

## A to F

**Adaptive clearing** (Adaptives Räumen): A clearing strategy in which the program keeps the load on the bit even, so that deep passes with the full cutting edge are possible. See [Operations](Operations).

**AI model** (KI-Modell, since 0.13.0): A file with the depth model for “Photo → relief” that calculates on your computer and is loaded, checked or removed in the “AI models” dialog. See [AI models and start page](AI-Models-and-Start-Page).

**Air cut** (Luftschnitt): The whole program runs raised and without spindle. A test run without contact with the material.

**Alarm**: State of the controller after a serious problem (for example soft limit exceeded). The controller is locked until you unlock it (`$X`) or perform homing. After an alarm the position can be lost.

**Array**: Several copies of a shape, arranged in a grid, on a circle or along a path.

**Ball-nose bit** (Kugelfräser): A bit with a hemispherical tip, for example for 3D reliefs.

**Baud rate** (Baudrate): Transmission speed of the serial connection to the controller. GRBL default and xPRO V5: 115200.

**Boolean operation** (Boolesche Operation): Combining shapes: weld (union), subtract, intersection, exclusion.

**Checklist** (Prüfliste): The list of errors, warnings and notes on the calculated toolpaths. Errors block export and machine start.

**Clamps** (Spannmittel): Toe clamps, screws, vacuum cups with which the workpiece is held.

**Clearance** (Spiel): The air gap between two interlocking parts, for example with finger joints (guide value 0.1 mm). The test coupon of the fit assistant provides the right value for your material. See [Sheets and furniture](Sheets-and-Furniture).

**Climb milling, conventional milling** (Gleichlauf, Gegenlauf): The two directions of rotation of the bit relative to the feed direction. With **climb milling** the chip starts thick and ends thin, the edge is usually cleaner, and the bit is pulled into the material. With **conventional milling** it starts thin and ends thick. The default in ortino.CAM is conventional milling. See [Operations](Operations).

**Component (relief)** (Komponente (Relief)): A layer of a relief made from a profile, a pattern or an image, which is added to, subtracted from or blended with the others. See [Modelling reliefs](Modelling-Reliefs).

**Compression bit, downcut spiral, upcut spiral** (Kompressionsfräser, Abwärtsspirale, Aufwärtsspirale): Types of bits with spiral flutes. They differ in where the chips are carried. For cutting through plywood, coated boards and hardwood, the selection helper of the [cutter library](Tools-and-Cutting-Data) names a compression bit first, then a downcut or upcut spiral. Each recommendation comes with its reason.

**Core hole** (Kernloch): The pre-drilled hole in which an internal thread is milled.

**Corner block (XYZ corner block)** (Eckblock, XYZ-Eckblock): An L-shaped block with which you can probe X, Y and Z in one go.

**Creator** (since 0.13.0): A generator that produces a workpiece from sheet material from a few inputs (parts with grooves, parts list, assembly notes). See [Creators](Creators).

**Customer records** (Kundenstamm): The list of your customers with number and address, from which the quote takes the address block. Stored only on your computer. See [Customers and quotes](Customers-and-Quotes).

**Depth per pass** (Zustellung): How deep the bit cuts per pass.

**Dogbone** (Hundeknochen): A small circular relief in an inside corner so that a square counterpart fits in although the round bit rounds the corner.

**Easy mode** (Einfach-Modus): Display mode with the most important settings and explanations. Expert mode shows everything.

**Edge band** (Kantenband): A strip that covers the narrow side of a furniture panel. It changes the cut size.

**Emergency stop** (Not-Aus): The hardware switch that cuts the power to the machine at once. The buttons in the program do not replace it.

**Engraving bit** (Gravierstichel): A very pointed bit for fine lines.

**Entry** (Einstich, Eintauchen): How the bit goes into the material: vertically, on a ramp or on a helical path (helix).

**Feed rate** (Vorschub): The speed at which the bit moves through the material (mm/min).

**Finger joint** (Fingerzinken): A corner joint with interlocking fingers. See [Sheets and furniture](Sheets-and-Furniture).

**FluidNC**: A free firmware for controllers with ESP32. It speaks a GRBL-compatible protocol.

## G to O

**G-code** (G-Code): The text language in which a controller receives movement commands (`G0` rapid, `G1` line, `G2` and `G3` arc, `M3` spindle on, `M5` spindle off). ortino.CAM produces it with the matching [post-processor](Post-Processors-and-Controllers).

**Grain** (Maserung): Fibre direction of the wood. It matters in sheet cutting and in the sheet planner.

**GRBL**: A widely used free firmware for router controllers. ortino.CAM talks to GRBL 1.1 and compatible controllers directly. **grblHAL** is a further development for more powerful control boards.

**Guillotine cut** (Guillotine-Schnitt): A cut that goes through the whole remaining area of a sheet, as on a panel saw. See [Sheet cutting](Sheet-Cutting).

**Height map** (Höhenkarte): A measurement of the height of the spoilboard at a grid of points. When milling, the tip of the bit follows the board. See [Fixed probe and spoilboard](Fixed-Probe-and-Spoilboard).

**Helix**: A helical path. You use it to plunge, to drill holes larger than the bit, or to mill a thread.

**Homing** (Referenzfahrt): The machine moves to the limit switches and then knows its position.

**Inlay**: Two matching parts: a recess in a sheet (female) and a mirrored insert (male) that fits into it.

**Island** (Insel): A piece of material that would be cut free all around after milling out, for example the middle of an O. In a stencil, **bridges** hold it to the surroundings. See [Drawing and importing](Drawing-and-Importing).

**Jogging (manual control)** (Handsteuerung, Jog): Moving the machine by hand in small steps with the keys or the mouse.

**Level by level, part by part** (Ebene für Ebene, Teil für Teil): see Order of the depth passes.

**Limit switches** (Endschalter): Switches at the ends of the axes with which the controller learns its position during homing.

**Lot** (Los): In the quote, one set of all parts of the project, all sheets milled once. The quantity is the number of lots.

**Machine coordinates and work coordinates** (Maschinenkoordinaten und Arbeitskoordinaten): Machine coordinates refer to the limit switches of the machine. Work coordinates (G54) refer to your work zero on the workpiece.

**MCP (Model Context Protocol)**: A standard with which AI programs such as Claude use tools of other programs. See [Claude, MCP and API](Claude-MCP-and-API).

**Nesting** (Schachteln): Arranging parts on sheets so that little space is wasted.

**Onion skin** (Restschicht): A thin layer that is left at the bottom when cutting out and is separated last.

**Operation** (Bearbeitung): An instruction to the program about what should happen with shapes (profile cut, pocket, drilling …). The toolpath is created from it.

**Order of the depth passes** (Zustellreihenfolge, since 0.13.0): Whether, with several parts, each part is milled to its final depth before the next one follows (**part by part**), or all parts go one step deeper first (**level by level**). See [Operations](Operations).

## P to Z

**Parallax** (Parallaxe): Apparent shift of an object when the camera sees it from a different angle than its surroundings. With the [camera](Camera-on-the-Worktable), the thickness of the material shifts the image outwards.

**Parametric sketch** (Parametrische Skizze): A drawing made of points, segments, circles and arcs whose shape is defined by dependencies and dimensions (also formulas). See [Drawing and importing](Drawing-and-Importing).

**Pocket** (Tasche): An operation that clears an area down to a depth.

**Post-processor** (Postprozessor): The profile that translates toolpaths into the G-code dialect of a controller.

**Price breaks** (Staffel, Staffelpreise): A table in the quote that shows the price per lot for several quantities, for example 1, 5, 10 and 25. Setup occurs only once, which is why the price per lot falls.

**Probing** (Antasten): The bit moves slowly onto a touch plate or a corner block until a contact signals that it has touched down. The program sets the work zero from this. See [Milling on the machine](Milling-on-the-Machine).

**Profile cut** (Profil): An operation that follows a contour: outside (cut out a part), inside (cut out a hole) or on the line (engraving).

**Rapid** (Eilgang): Fast movement without cutting, for example between two paths.

**Rhai**: The built-in scripting language for your own tools.

**Safe height** (Sicherheitshöhe): The height above the workpiece at which the bit travels for rapids.

**Saw plan** (Sägeplan): The plan of how rectangular parts are sawn from sheets with through cuts. See [Sheet cutting](Sheet-Cutting).

**Serial number** (Seriennummer): A counter in the text, for example `{n:001}`. It counts up in arrays and series (001, 002, 003 …).

**Sheet** (Platte): In ortino.CAM, the material you mill from (size, thickness, material, work zero).

**Soft limits** (Soft-Limits): A setting of the controller that prevents movements beyond the travel. It needs a homing.

**Spindle** (Spindel): The motor that turns the bit.

**Spindle speed** (Drehzahl): Revolutions of the spindle per minute (rpm). It depends on the bit and the material.

**Spoilboard** (Opferplatte): The board on the machine table that the bit may cut into when cutting through. It protects the table.

**Start check** (Start-Check): Checks the state of the controller against your project before every run. Errors block the start.

**Start page** (Startseite, since 0.13.0): The welcome view with the quick access buttons; the Home button in the header bar (`Alt+Home`) always takes you back there. See [AI models and start page](AI-Models-and-Start-Page).

**Stencil bridge** (Schablonen-Steg): A narrow bridge of material that holds an island in a stencil letter to the surroundings. See [Drawing and importing](Drawing-and-Importing).

**Stepover** (Bahnabstand): Lateral distance between two adjacent milling paths, usually in percent of the bit diameter.

**STL, 3MF**: File formats for 3D bodies. ortino.CAM reads STL (and STEP) and writes STL and 3MF. See [Exporting 3D bodies](Export-STL-3MF-en).

**Tab** (Haltesteg): A bridge left standing that holds a cut-out part to the rest of the sheet until you separate it by hand.

**Toolpath** (Werkzeugweg): The calculated path of the bit.

**Touch plate** (Tastplatte): A flat metal plate of known thickness for probing Z.

**Travel** (Verfahrweg): The longest distance an axis can move.

**V-carving**: An operation with a V-shaped bit in which the cutting depth follows the width of the shape.

**Work zero (workpiece zero)** (Nullpunkt, Werkstücknullpunkt): The point from which all coordinates of the program count. In X and Y usually a corner of the workpiece, in Z the surface (or the table).

**Z zero** (Z-Null): The height that counts as zero for Z: either the top of the sheet or the table (the spoilboard). See [Milling on the machine](Milling-on-the-Machine).

**`.ocam`, `.ocamd`:** File extensions. `.ocam` is a project, `.ocamd` a design package for the [community portal](Community-Portal-en).
