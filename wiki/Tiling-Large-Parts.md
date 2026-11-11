**English** | [Deutsch](Grosse-Teile-kacheln)

# Tiling large parts (since 0.7.0)

> **Honest about the status:** The tiling has only been checked against geometry and property tests, the simulation, the built-in machine simulator and Chromium. **Never on a real machine** and not under Windows (WebView2). How exactly the tiles fit together at the seam depends on how exactly the bit stands over a registration mark, how straight the material lies after moving and how flat sheet and spoilboard are; that is **not tested**.

If a workpiece is larger than the **travel** of your machine (for example 2400 × 1200 mm on a 600 × 400 mm CNC router), ortino.CAM splits it into **tiles with overlap** and produces a program for each tile. Between two tiles you move the material by the **feed distance** and clamp it again; two **registration marks** that the previous tile has drilled determine the XY zero of the new tile.

## Procedure at the table

1. **Tile 1:** Clamp the material so that tile 1 lies within the travel, set the XY zero at the corner of the sheet, probe Z, mill. Afterwards the program drills two small **registration marks** into the overlap with tile 2.
2. **Moving:** Release the material, move it by the feed distance shown (best against a straight stop bar so that it does not twist), clamp it. The distance does not have to be exact; it only has to bring tile 2 into the travel.
3. **Tile 2:** Move the bit (spindle off) over **registration mark 1**, centre it and set the XY zero there; then confirm the position at **registration mark 2**. If it deviates by more than the tolerance (default 0.3 mm), the pre-flight check blocks the tile: then the material is twisted or the bit was not standing centred over mark 1. Mill, and so on up to the last tile.

## Good to know

* **3D relief, adaptive clearing, rest machining and inlay** work only if they lie **completely within one tile**.
* Setup sheet and instructions know the tiles; the simulation runs over all tiles.
* Never skip the check at mark 2. **The first time on an offcut with two tiles**, running the seam through waste.

Related: [Double-Sided Milling](Double-Sided-Milling) (several set-ups with shared reference points), [Milling on the Machine](Milling-on-the-Machine), [Setup Sheet and Quote](Setup-Sheet-and-Quote).

<!-- videos:start -->
## Videos

* [![Tile parts larger than the machine travel (video, English captions)](https://klapsc.github.io/ortino-cam/videos/tiling-poster.jpg)](https://klapsc.github.io/ortino-cam/videos/#tiling)  
**Tile parts larger than the machine travel** · 17 s

All videos: [Videos](Videos-en).
<!-- videos:end -->
