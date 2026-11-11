**English** | [Deutsch](Eigene-Vorlagen)

# Custom templates and the “Shapes” dialog (since 0.15.0)

In the **Pattern Studio** and the **Relief Studio** you can save a state you have set up as a **custom template** and use it again later. There is also a new dialog, **“Shapes”**, with ten basic shapes. Custom templates are in the **“Own”** section, the first tab of the gallery. The [Shape and Pattern Generator](Shape-and-Pattern-Generator) in the browser reads and writes the same file, so you can import templates saved there into the program.

> **Honest about the status:** Everything is checked with tests (Vitest) and in the browser (Chromium) with the real calculation core, also with files produced by the code of the web generator. **None of it was milled.** **Never checked under Windows (WebView2):** whether saved templates survive a restart, an update or a Windows clean-up there, whether the file download shows a save dialog there and whether dropping files works there. **If you want to be safe, save a file with “Save all” and keep it.**

## Saving a template

1. Open the **Pattern Studio** or the **Relief Studio** (tool palette or command palette `Ctrl+K`: “Patterns & reliefs …”) or the **“Shapes”** dialog (below) and set up what you want to keep.
2. At the top right choose **“Save as own template”** and enter a name (at most 80 characters; type and date are suggested).
3. The template then appears in the **“Own”** section, newest first. The same template is not saved twice.

What is saved:

* **Pattern:** the pattern type, the random value (seed), **all** settings as numbers and the area (also rotation, text and font, as far as set). For the **word and logo collage** (since 0.16.0) the four entries are added, for words with text, font, bold and frequency; a logo slot stays without an image.
* **Relief:** size, depth, random value, sliders, post-processing, rim and the layers with their sources and settings.
* **Shape:** the shape with its dimensions (millimetres) and settings.

## The “Own” section

* **Cards** with a preview (patterns and reliefs are calculated live by the calculation core like the other cards, shapes as a drawing with arcs), name, date and dimensions. One click **uses** the template.
* **Rename**, **Save as file** (one template), **Delete** (with a confirmation; if you have not saved it as a file, it is gone afterwards).
* **Import:** choose files (up to ten at once) or drag them onto the section. Patterns, shapes and reliefs from a file each land in the section of their own picker; the message counts by type. Importing the same template again changes nothing.
* **Save all:** all custom templates into one file.
* **Create new:** starts with the default values (for a pattern those of the chosen type, for a relief one layer, for a shape the basic shape); for pattern and relief the “Advanced” section opens.
* The line “x of 200 templates saved” shows how much room is left.

**Using:** A custom template is placed like a bundled one. A pattern arrives in the middle of the area at the size of the template (at most the chosen area); after that it can be changed, and “Set up machining” works as usual. A relief becomes at most 90 % of the sheet in size, centred, with at most 60 % of the sheet thickness as depth. Values outside the ranges of this program version are limited, unknown ones are dropped; the program says so with “Not applied: …”. If this program version does not know the pattern type or the source of a template, the card shows “not available” with the reason.

## The “Shapes” dialog

The **“Shapes”** dialog has existed since 0.15.0. You open it in the “Design” step through the command palette (`Ctrl+K`: “Shapes: basic and own …”) or through the Shapes icon in the header of the Pattern Studio gallery. It offers ten basic shapes: **rectangle, rounded rectangle, circle, ellipse, polygon, star, heart, gear, rosette and slot**. You set the dimensions in millimetres, see the preview and place the shape in the middle of the active sheet with **“Add to sheet”**. Shapes too can be saved as a custom template.

* Rectangle (also rounded and as a slot), circle, ellipse, polygon and star arrive on the sheet as the corresponding **shapes of the program**; heart, gear, rosette and also polygon and star with a corner radius arrive as a path. Roundings stay **true circular arcs**, not many small segments.
* The **gear** is a decorative shape with trapezoid teeth, **not a working gear**. The **heart** has a fixed aspect ratio (height about 0.91 · width).
* If an input does not fit (for example an inner diameter larger than the diameter), the dialog says so with the fix; a radius that is too large is limited, with a note.
* If the shape is larger than the sheet, the dialog warns.

## Files and exchange

A template is a **JSON file** (UTF-8) with the extension `.ortino-vorlage.json`. It names the format (`ortino-vorlage`, version 1), the type (`muster`, `form` or `relief`), the name, the time and the settings (only numbers, texts and truth values, never images and never anything that is executed). **Save all** writes a file `ortino-vorlagen-<date>.ortino-vorlage.json` with the list. The program checks every file strictly: at most 1 MB, at most 200 templates per file, valid characters in the name, known fields. A broken file or a broken entry gives a message with cause and fix, never a crash; if a file has a newer version than the program knows, it says so and asks for an update. Since 0.16.0 a pattern of the word and logo collage may carry an optional field `items` (up to four entries, never an image); the format stays version 1. Program version 0.15.0 rejects a file with `items` on import (unknown field); all files without a collage read unchanged. Because the format is the same, you can import files from the [online generator](Shape-and-Pattern-Generator) here (shapes stay real shapes) and pass on files from the program.

## Where the templates are stored

Custom templates are in the program’s **interface storage** (`localStorage`, as for a web page in a browser), up to 200 templates and about 2 MB. They are **not** in the data folder, **not** in the project and **not** in the [Backup in the portal](Backup-in-the-Portal), and they do not move to another computer by themselves. If the storage is not usable, the program keeps working with the templates as long as it is open, and says so. If the saved list is not readable, the program skips it, does not overwrite it blindly and keeps a copy.

**Windows (WebView2):** The storage belongs to the profile of the program window. Whether the templates survive a restart, an update or a clean-up of the WebView2 data there is **not checked**. So: **“Save all” and keep the file**, especially before an update.

## Limits

* **Patterns from an image** (“Image as hole grid”) cannot be saved: image data does not belong in a template. The button says so. The same applies to a **word and logo collage with a logo image**; you can save the words (without the image) or the whole pattern as a project.
* **Reliefs:** Of the 62 bundled templates, 60 can be saved, not **“Image → relief”** and **“Dome shapes”**. Reliefs from a **photo**, **height image**, **3D model**, a **mask**, from **components** or with **brush strokes** are rejected: the button is then locked and names the cause.
* A template holds **settings**, no sheet and no position on the sheet.
* At most **200 templates** and about **2 MB** in storage, a file at most **1 MB**.
* Not in the Web Designer of the portal.
* Everything only calculated, **nothing milled**; the traffic-light check of the Pattern Studio and the key figures of the Relief Studio are measurements on screen.

## Next

* [Drawing and importing](Drawing-and-Importing) (Pattern Studio)
* [Operations](Operations) (Relief Studio)
* [Shape and Pattern Generator](Shape-and-Pattern-Generator) (in the browser)
* [Backup in the portal](Backup-in-the-Portal)
