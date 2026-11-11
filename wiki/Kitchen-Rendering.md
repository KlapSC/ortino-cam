**English** | [Deutsch](Kuechen-Rendering)

# Kitchen Rendering

The furniture and kitchen designer ([Sheets and Furniture](Sheets-and-Furniture)) can save an **image of the kitchen**, with light, soft shadows, gloss of painted fronts, built-in sink with tap, floor, walls and splashback. It is meant for the conversation with the customer: “This is how your kitchen could look.”

> **Honest about the status:** This is a **quick WebGL image**, **not a photorealistic render**: no true global illumination (no scattered light from wall to wall), no refraction of light, no reflection of the kitchen in the floor. **Colours on the screen are not colour samples.** Customers should see a sample of the real paint. The rendering was **checked only in Chromium with software graphics**, never under Windows (WebView2) and never on a real graphics card; how long “Standard” and “High” take at 4K has not been measured.

## Opening

In the furniture designer: the **camera button** in the header bar, the `R` key or the command palette (`Ctrl+K`, “Export rendering …”). Without cabinets there is nothing to render. The dialog shows a rough, rotatable preview on the left (dragging rotates, mouse wheel zooms) and the settings on the right; **Render and save** calculates the image in final quality.

## Settings

* **Size:** Full HD, 4K, Square or Custom. Large images are calculated in tiles; from about 20 megapixels the dialog warns about duration and memory.
* **View:** Front, Angled, Room corner, the current 3D view or an own view; focal length 14 to 135 mm; doors open if you want.
* **Quality:** Draft, Standard or High (more passes: softer shadows, more gloss, longer calculation time).
* **Light:** Daylight from the window, Warm evening mood or Neutral studio; plus switchable **LED strips** under the wall cabinets.
* **Room:** floor (four variants), wall colour, walls back / left / both, optional splashback (tiles, dark glass, light glass, stainless steel).
* **Sink:** It comes from the **cutout of the worktop** (Kitchen → Worktop): stainless steel with one or two bowls, drainer and tap. Without a cutout there is no sink; a hob cutout gives a hob.
* **Colours and gloss:** The surfaces of the fronts, the carcass and the worktop (see [Sheets and Furniture](Sheets-and-Furniture)) are taken over: clear-coat gloss depending on the gloss level, metal for handles, dark fronts with visible reflections.
* **Output:** PNG or JPEG, file name, if you want the line “Representation · dimensions and colours not binding” at the bottom of the image.

## Notes

* During rendering the dialog shows the image as it forms and a progress bar. **Esc** cancels (then nothing is saved).
* It is saved as a **download**; Windows or the browser decides the target folder (usually “Downloads”).
* The test images in the tests still look plain: the sink is convincing mainly in close-up, the LED strips give a soft warm haze instead of a cone of light, and with high gloss a lamp appears as a round bright spot on a front.
* Reliefs on fronts appear in the image as gentle shading (the front stays flat).
* **Furniture:** If the design consists only of pieces of furniture ([Furniture Designer](Furniture-Designer)), the rendering shows a **furniture scene** instead of the kitchen: parquet, wall behind the rearmost wall piece, side walls, selectable rug and wood grain along the fibre. Splashback and LED strips are omitted. The limits are the same (software graphics in Chromium, never checked under Windows).

<!-- videos:start -->
## Videos

* [![Design a kitchen with the cabinet designer (video, English captions)](https://klapsc.github.io/ortino-cam/videos/kitchen-designer-poster.jpg)](https://klapsc.github.io/ortino-cam/videos/#kitchen-designer)  
**Design a kitchen with the cabinet designer** · 17 s

All videos: [Videos](Videos-en).
<!-- videos:end -->

## Next

* [Sheets and Furniture](Sheets-and-Furniture)
* [Furniture Designer](Furniture-Designer)
* [Keyboard Shortcuts](Keyboard-Shortcuts)
* [Troubleshooting](Troubleshooting)
