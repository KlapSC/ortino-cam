**English** | [Deutsch](Foto-zu-Relief)

# Photo → relief (AI depth estimation on your computer)

Since version 0.6.0, ortino.CAM can turn a **photo** into a **relief**: A small AI model (Depth Anything V2 Small) estimates how far away each spot in the picture is. From that a height image is made, which enters the project as an ordinary relief and can be edited further and milled in the Relief Studio.

> **Honest about the status:** The result is an **estimate, not real geometry.** For scenes with spatial depth (objects, landscapes, heads from the side) it is usable; for **flat subjects photographed head-on** it is weak. It was only checked with self-built scenes and tests, **not with real photos**, **not on Windows**, and **none of it has been milled**. Mill a test piece first.

## How it works

1. In the **Relief Studio**, choose the card **“Photo → relief”** in the gallery (or `Ctrl+K` → “Photo → relief (estimate depth) …”). It does not exist in the Web Designer of the portal.
2. **The first time**, the program asks your portal whether the **depth model** is there (a small request without a photo) and offers it for **download** (47.3 MB, with progress, cancel and resume; the file is checked against a fixed checksum). Without a network: **“Use a model file …”** (file from a USB stick). If the model is not yet on your portal, the dialog gives the reason with a solution; then the operator has to provide it.
3. **Choose a photo or drag it in** (JPEG, PNG, WebP; the orientation of phone photos is respected; transparent parts become ground). An estimate takes roughly two to six seconds on a computer with four cores, three to four times as long at the “Fine” level; you can cancel.
4. You see **three views**: photo, depth map (light = high) and a shaded preview of the relief.
5. **Sliders** on the right: depth in mm, invert, flatten background, smooth, contrast, depth compression, “Remove base curvature” (for flat subjects from the front) and the resolution.
6. **Insert as relief** (`Ctrl+Enter`): A relief with one image layer is created (one undo step). “Insert and open in the studio” then opens the Relief Studio for further editing (mix with patterns, mask, edge falloff, “Set up machining …”).

## Managing the model in the menu (since 0.13.0)

> In version 0.12.0 and earlier versions you load and remove the model only in the dialog “Photo → relief”.

Since version 0.13.0 there is a dialog of its own for this: **Extras ▸ AI models …** (also `Ctrl+K` “AI models”, **Settings ▸ General** and a tile on the start page). There you see the state, size, licence and location of the depth model and whether it is available on your portal, and you can **download** it (with cancel and resume), **check again**, **add it by hand** or **remove** it. Nothing is ever downloaded without your click. In the Art Designer, the button **“Load model …”** (at “Estimate depth (AI)”) leads to the same card. Everything else is on [AI models and start page](AI-Models-and-Start-Page); nobody has yet checked the download of the real model from the real portal.

## Good to know

* **The photo never leaves your computer.** The calculation runs in the program. Only the request whether the model is there, and the download of the model, go to the portal. The **original photo is not stored in the project**, only the calculated height image.
* **Rights to the picture:** For photos of people you need the consent of the people shown, for other people's photos the permission of the author.
* **Glass, mirrors, water, sky** are estimated poorly by the model.
* **Licence of the model:** The weights are under Apache-2.0. The training data also include collections with research or non-commercial terms; whether these carry over to the weights is legally unresolved (note also in the dialog).
* **Removing the model:** at the bottom right of the dialog; existing reliefs stay unchanged.

## For operators of their own portal

The model has to go onto the portal once: workflow **“Modell bereitstellen”** (provide model; the workflow is named in German) with “hochladen” (upload), or `node scripts/modell-hochladen.mjs` with the deploy token. After that, `https://<portal>/api/v1/models/depth-anything-v2-small-fp16-v1.onnx` must answer with 200 and a size of 49,619,602 bytes. Details are in the portal's operating manual in the source repository.

## Troubleshooting

| Symptom | Solution |
|---|---|
| “The model is not on your portal yet” | Ask the operator to provide it, or add the model file by hand. |
| “different version” (size does not match) | Portal and program do not belong together; update program and portal. |
| “The portal cannot be reached right now” | Check the connection, then “Check again”; or add it by hand. |
| The relief is just a bulge | The subject was photographed too flat: try “Remove base curvature”, photograph differently (at an angle, with light from the side). |
