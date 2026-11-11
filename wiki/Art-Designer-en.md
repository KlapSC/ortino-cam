**English** | [Deutsch](Art-Designer)

# Art Designer (wall art in wood)

Since version 0.9.0 the menu **Create → Art Designer …** (or `Ctrl+K` → “Art Designer”) has a dialog that makes a **wall picture in wood** in five steps: as a **carved relief** from one block or as a **layered plywood picture** from stacked plywood layers. It builds on the Relief Studio and does not replace it. **Since 0.14.0** there are **14 motifs instead of 8**; the six new ones are marked below.

> **Honest about the status:** Everything is **calculated and checked on screen, nothing was milled or glued.** Machinability (steepest flank up to about 67°, smallest inner radius from about 1.8 mm) is a calculated value, not a value from experience. It was checked with tests, the simulator and Chromium, **not under Windows (WebView2) and not on a real machine.** The motifs are **the program’s own patterns, generated on the computer**; they are reminiscent of wall pictures in wood, but they are not copies, and not all of them turned out equally well. This also applies to the six motifs since 0.14.0. Test with a piece of scrap wood first.

## How it works

1. **Format:** Choose a group (A series, Poster 30 × 40 to 100 × 140 cm, Square, Panorama or **Custom size** from 50 to 3000 mm), portrait or landscape, and sheet thickness. Each motif has a recommended format.
2. **Motif:** The motifs are on the left with a preview image. With the sliders **Size, Density, Softness, Variation** and **Depth** you change the picture; the **dice** (random) makes a new one. The number next to the dice (seed) pins a picture down.
3. **Frame and edge:** Rim width (0 = no rim), **Fade-out** (the relief rises gently towards the rim), outer edge straight or with a **chamfer**.
4. **Text and signature:** Text, size and position in the rim (bottom centre, left or right); it is **engraved**.
5. **Finish:** The summary shows sheet, motif and notes. **“Add to project”** is one undo step; **“Add and set up machining”** also creates roughing and finishing (as in the Relief Studio, see [Modelling reliefs](Modelling-Reliefs) and [Operations](Operations)).

The preview shows **“Ball nose up to Ø …”**: with a larger bit, fine grooves are lost. Below the preview are **notes with a fix**, for example about flanks that are too steep or sheets that are too large (the sheet is larger than the machine’s work area: choose a smaller format or machine in several setups, see [Tiling large parts](Tiling-Large-Parts)).

## The 14 motifs

| Motif | Picture |
|---|---|
| **Leaf stream** | many curved, overlapping leaves in a current, veins as grooves; best in landscape |
| **Leaf branch** | a few large leaves on a slender S-shaped branch, calm (formerly “Leaf swirl”) |
| **Monstera** | large heart-shaped leaves with slits and holes (the weakest of the first eight motifs) |
| **Ginkgo** | fan-shaped leaves with folds on a curved branch |
| **Fern** | feathered fronds fanning out from one point; dense and pointed |
| **Palm fronds** | fronds with leaflets along a raised midrib |
| **Feather fan** | long ribbons fanning out from a few points |
| **Flowing ribbons** | waves of ribbons with fine joints |
| **Layered mountains** *(since 0.14.0)* | several mountain ranges one behind the other with pointed peaks and round valleys, higher at the back, plus a small disc (sun or moon) in the sky; recommended landscape, 60 × 90 cm. The clearest of the new motifs as a layered plywood picture; as a carved relief the surfaces are flat and only the edges of the steps are visible |
| **Sunrise** *(since 0.14.0)* | half a sun on the horizon, long and short rays alternating, several wave bands in front; recommended landscape, 60 × 90 cm. Graphically clear; the narrow rays as layered plywood were not checked in the picture |
| **Moon and clouds** *(since 0.14.0)* | crescent moon with a halo, small four-pointed stars and cloud bands made of arcs in a row; recommended portrait, 50 × 70 cm |
| **Moon phases** *(since 0.14.0)* | five moons in a row, waxing lit on the right, waning lit on the left; recommended landscape, panorama 40 × 100 cm. More of a symbol than a landscape picture; uses only three steps, so only a few layers |
| **Olive branch** *(since 0.14.0)* | curved branch with pairs of lance-shaped leaves and olives, a second, deeper branch behind it; recommended portrait, 50 × 70 cm. **Schematic** (even pairs, simple ovals as olives) and, as layered plywood, many small islands |
| **Grasses and pampas** *(since 0.14.0)* | tufts of drooping blades, above them blades with pampas plumes; recommended portrait, 50 × 70 cm. The impression is closer to the fern than to grass in the wind; the plumes have only coarse grooves |

The **landscapes** (mountains, sunrise, moon and clouds, moon phases) consist of a few flat steps and are meant for **layered plywood**: each step gives one layer, and the number of layers should be at least as large as the number of steps (otherwise neighbouring steps are merged). All the new motifs carry a recommended format and orientation; you can deviate from them. None of them was milled.

Everything is a **height field** (as in the Relief Studio), so it can be machined from above with a ball nose bit; there are no undercuts and no pierced sheets.

## Layered plywood

In the **Motif** step you switch from **Carved** to **Plywood layers**. The motif is then split into **3 to 24 layers** of plywood (thickness 3, 4 or 6 mm), plus a **backer** (3 to 40 mm).

* **Layers:** Each layer consists of a frame piece with holes and individual islands. The step **“Layers”** shows them one at a time, with the others faintly underneath.
* **Alignment pins** for lining up, **numbers** on the parts, optionally a **gluing guide**.
* **Plywood sheets:** The parts are distributed over sheets; you choose the format yourself (default: the machine’s work area). **If a part does not fit on the sheet** (for example a picture of 50 × 70 cm on a machine with a work area of 600 × 400 mm), the program reports an error with a fix, and “Add to project” stays locked until a larger sheet format is chosen.
* **Assembly plan:** Text and a list with the order for gluing, which you can copy.
* **Adding** creates the backer and the plywood sheets with the machining jobs (one undo step).
* **Fade-out and chamfer do not apply:** Each layer has a vertical edge; you break the edge by hand if needed. The **lettering** stays (V-carving into the top layer, with a 60° V-bit).

**Limits of layered plywood:** For almost all motifs the top layer consists of the frame only. Ginkgo and Fern have very thin webs in the upper layers (the program warns about “thin spots”). In portrait format the Leaf stream is sparsely filled from the fourth layer on. Parts inside the holes of other parts are not nested, so the waste is higher than with [Sheets and furniture](Sheets-and-Furniture).

## Your own image (from 0.10.0)

In the **Motif** step there is the section **“Your own image”**. You choose a file (PNG, JPEG or WebP) or drag it onto the dialog. The program reduces it to at most 1024 pixels before calculating. **The brightness of the image is the height:** light = high, dark = low.

* **Position:** Sliders for left–right, bottom–top, **size** and **rotation**; in the top view you move the image with the mouse and scale it with the mouse wheel (also arrow keys and +/−).
* **Blending into the pattern:** You choose the **side** (whole image, left, right, top or bottom half, or centre) and set the **boundary**, the **softness of the transition** and the **image share**. This way a face can be drawn as an image on one half and show only the pattern on the other. Optionally: an image edge that fades out softly, and “Pattern under the image”.
* **Tone** (under “More”): contrast, gamma, blur, invert.
* **Estimate depth (AI):** for photos, if the depth model from **Photo → relief** is present; otherwise the choice is locked, with a note.
* Works in **Carved** mode and in **Plywood layers** (where the soft transition becomes narrow bands, one per layer thickness).

**Honest about the result:** A face seen from the front gives only a **flat relief** as brightness, more a gentle seal than a portrait. Side views and images with clear light and dark areas work better. A **dark background** becomes a deep ground (the image then sits in a hollow): use a light background or “Invert”. **Hard edges** (softness 0) are vertical walls and can only be machined as a step; for photos with a lot of structure, increase the blur. Transparency does not count (see-through parts turn white). The image belongs to the open dialog; when you close it, it is gone. **None of this was milled;** the AI estimate was not checked with the real model. For photos of people you need the consent of the people shown, for other people’s images the permission of the author.

## Good to know

* **Only in the program,** not in the [Web Designer of the portal](Web-Designer-in-the-Portal).
* With Claude: the Art Designer can be reached through the local interface (`art.formats`, `art.plan`, `art.layers`, `art.assembly`, `art.create`; the image through `motif.image`); see [Claude, MCP and API](Claude-MCP-and-API).
* The 3D preview is slow without a graphics card.

Next: [Modelling reliefs](Modelling-Reliefs), [Photo → relief](Photo-to-Relief), [Checking and simulation](Checking-and-Simulation).
