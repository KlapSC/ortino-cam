**English** | [Deutsch](3D-Modelle-importieren)

# Importing 3D models (STL and STEP)

A 3D model from a CAD or mesh program can be brought onto the sheet in ortino.CAM, as a **3D relief**, as an **outline** or as a **layered model**. Before that you see it in 3D in the dialog, align it, and get a checklist with suggested solutions.

> **Honest about the status:** All of this was **only checked against tests, the simulator and Chromium**, with self-generated bodies (box, sphere, cone, pyramid, mushroom) and small self-built files. **It has never been milled** and **never tried with a model from a real CAD program** (Fusion, SolidWorks, Blender, FreeCAD …). The **STEP import** is code of our own and was only checked with self-written example files in the style of the exporters. Whether your model arrives complete and true to size is shown by the report and the checklist in the dialog. Look at the result in the step “Check” before you mill, and start with an offcut.

## Opening

*File ▸ Import 3D model (STL, STEP) …*, *File ▸ Import (SVG, DXF, PDF/AI, image) …* (`Ctrl+I`) with a `.stl`, `.step` or `.stp` file, the command palette (“Import 3D model”), or simply **drag the file into the window**.

## In the dialog

On the left the 3D view (rotate, move, zoom with mouse, finger or pen): the model, the sheet as a rectangle with thickness and a frame with the dimensions. On the right the settings:

1. **Orientation:** which side faces up (Top, Bottom, Front, Back, Left, Right), rotating about any axis, mirroring.
2. **Size:** unit of the file (mm, cm, inch, m), scale in percent, *Fit to sheet*, *Fit to material thickness*. An STL file has no unit: the program **suggests one** (with a note), the choice stays with you. STEP files bring their unit with them.
3. **Placement:** position on the sheet and, for the relief, the height in the material (top flush, or the model sunk in).
4. **Conversion:** three cards, see below.
5. **Check:** list with notes, warnings and errors, each with a **solution** and, where possible, a button that applies it (“Scale to 62 %”, “Rotate by 90°”, “Unit cm”).

In **easy mode** you see side facing up, unit and scale, the cards and the check; the rest is behind “More settings”. *Importing* (`Ctrl+Enter`) is a single undo step, *Cancel* or `Esc` leaves the project untouched. Without WebGL the dialog shows a message instead of the view; dimensions, check and import still work.

## Three ways of converting

* **3D relief:** The model is mapped onto a grid **from above**; at each point the topmost surface counts. The result is an ordinary relief, roughing and finishing work as with any relief (see [Operations](Operations)), and can be set up right away if you wish. It is calculated directly from the mesh, not via an 8-bit image, which would be too coarse for models. If the depth is smaller than the model, it is cut off at the bottom; the default is the model height, at most **three quarters of the sheet thickness**, so that a floor remains.
* **Outline as shape:** the **shadow from above** as a closed contour with holes, if you wish with a profile operation set up right away (outside around the contour, holes from the inside). Arcs stay arcs where the model has them.
* **Layered model:** the model is cut into **layers of the sheet thickness**, each layer as a profile on a sheet of its own or all side by side on one sheet. At most 200 layers. The layers have **no dowel holes**; you have to align and glue them yourself.

## The checklist

Among other things it reports: unit only guessed, very small or very large, too flat, **wider or deeper than the sheet**, **taller than the material thickness**, too little floor, **undercuts** (an estimate: the share of the surface that a router cannot reach from above), **open edges or holes in the mesh**, several separate parts, resolution too coarse for the bit, and details that the ball-nose bit does not form. A mesh that the program cannot close is **not repaired**: the list names the problem, the solution lies in the mesh software.

## STEP

Reading is **code of our own without a third-party library** and understands the common exchange formats (AP203, AP214, AP242): planes, cylinders, cones, spheres, tori, B-spline, extrusion and revolution surfaces, ready-made meshes, simple assemblies and the units. The dialog shows a **STEP report**: how many surfaces were converted, what is not supported, detected unit and program, volume, whether the mesh is closed. A surface that the program does not know is dropped and counted; the mesh is then open, the report says so, and the dialog suggests also exporting the file as STL. **Only if all surfaces have been converted and the mesh is closed has the model arrived completely.**

Not supported are, among others, hyperbola and parabola curves, bodies made from construction rules (CSG), pure wireframe models, compressed files (`.stpz`) and files over 200 MB. Colours, layers, dimensions and names are not read. Several bodies (and the parts of an assembly) are joined into **one** mesh, not fused.

## Limits

* Top view only: undercuts are reported, not milled. Milling two sides is a separate route ([Double-sided milling](Double-Sided-Milling)), not connected here.
* Scale only uniform in all axes.
* The mesh **cannot be edited** (fill holes, simplify, repair).
* **Export:** Since 0.11.0, imported models, furniture parts (as sheet bodies, without bores and handles) and relief sheets can be saved as **STL and 3MF** (File menu, Furniture Designer, Relief Studio, command line `ortino export --format 3mf`). Only checked against tests, nothing with a slicer, CAD program or printer. **Not** to STEP; 3MF cannot be read in. Details are under [Exporting 3D bodies: STL and 3MF](Export-STL-3MF-en).
* **Not measured:** the memory requirement for very large models (upper limit five million triangles), models with very many small or intersecting parts, and real CAD files.

## See also

* [Drawing and importing](Drawing-and-Importing)
* [Exporting 3D bodies: STL and 3MF](Export-STL-3MF-en)
* [Operations](Operations) (milling a 3D relief)
* [Checking and simulation](Checking-and-Simulation)
