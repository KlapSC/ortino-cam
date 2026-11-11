**English** | [Deutsch](Kamera-auf-der-Arbeitsplatte)

# Camera on the worktable

A USB camera above the machine delivers an image of the work surface. **Four QR markers** in the corners anchor it in millimetres. The program calculates perspective and scale, **rectifies** the image and puts it **under your design**. This way you position parts on the real material (an offcut, a crooked board, a printed sheet). The program can also detect the **outline of a workpiece** and take it over as a shape or remnant.

> **Honest about the status:** The camera function has **never been tested with a real camera**. It was checked with calculated images (a generated scene with a known perspective) and a test camera that a browser simulates (no real hardware). The behaviour of real cameras and drivers, lens distortion, autofocus, exposure control, reflections in the workpiece and the **Windows camera permission** are **untested**. The dialog says so too. Check the accuracy on a test piece before milling.

## How accurate is it?

On generated images the error is below 0.02 mm under ideal conditions. That is the **upper bound of the method, not the accuracy of a real camera**: the test images are made with the same model that the calculation fits. With a real camera, lens distortion, focus, exposure, print accuracy and the flatness of the markers determine the result. **Expect 0.5 to 1.5 mm** until you have measured it on your camera (check value, check grid, test piece).

## Setting up in five steps

You open the dialog through the button in the tool palette on the left of the drawing area (“Design” step), through the icon in the header bar or the command palette (`Ctrl+K`, “Camera above the work area”). It has four tabs: **Camera**, **Calibrate**, **Background**, **Outline**.

1. **Start the camera.** “Camera” tab: choose the camera and “Start camera”. The camera starts only on a button press and is released when you close the dialog. Without a camera you use **“Image from file …”** (PNG, JPEG or WebP), for example a photo from your phone.
2. **Print the sheet with markers.** “Calibrate” tab: the program generates a sheet (A4, as PDF or SVG) with the four markers. Side length 30 to 100 mm, default 50 mm. Print at **100 %**, not with “fit to page”. At the bottom is a 100 mm scale for checking.
3. **Place the markers in the corners.** Cut out the markers and place the **outer edge of the code** at the corner of the work surface. They must lie flat and matt, at the **height of the material surface** (see parallax below). A marker may lie rotated. If they lie somewhere else, you enter the centre points under “More settings”.
4. **Capture and check.** The result shows the quality, the **mean and largest error in millimetres**, a **check value** and notes (print size wrong, markers too small, marker at the edge …). The detected markers (green) and their target position (orange) lie over the image.
5. **Save the calibration.** Only the mapping (nine numbers) is saved in the machine profile, **never an image**.

The markers are numbered: **1 front left, 2 front right, 3 back right, 4 back left** (view from above, X to the right, Y to the back). With three usable markers it works with a warning; four are better. The program **does not guess**: if the assignment is not unambiguous, you get an error message instead of a guessed result.

## Background and outline

* **Background:** “Show camera image” puts the rectified image with adjustable opacity under the design. It is a **single frame**, not a live image: with “Update image” you take a new one. The image appears only on screen, **neither in the project file nor in the G-code**. After a restart the background is empty until you capture it again. You set the **position of the sheet** on the work surface here. The program calculates for you where the work zero has to be at the machine.
* **Outline:** “Detect outline” finds the workpiece by its colour difference from the bed. You take it over with “Insert as shape” (one undo step) or “Add as remnant” (for the sheet planner, see [Sheets and furniture](Sheets-and-Furniture)). Only the largest workpiece is detected, holes are filled. An image of the empty bed as a comparison helps with similar colours.

In Easy mode only the most important steps are visible. The rest is behind “More settings”.

## Limits you should know

* **Parallax:** The calibration holds for the **plane of the markers**. If the surface of the material is higher, it appears shifted outwards from the camera’s point of view. At a camera height of 1 m and 360 mm distance from the centre, that is about 1.1 mm for a 3 mm thick sheet, about **6.5 mm** for an 18 mm sheet and about 14 mm for a 40 mm block. **Fix:** place the markers at the height of the material surface (for example on spacers of the same thickness) or mount the camera higher. There is no calculated correction.
* **Lens distortion** is not corrected. Wide-angle and action cameras often distort by several millimetres at the image edge. Mount the camera high, use the “check grid” (curved lines show distortion) and mind the check value.
* **Lighting:** even, soft light without gloss, matt printed markers. Reflective sheets, hard shadows and backlight disturb the detection. The camera should not “hunt” with auto exposure.
* **Resolution:** The program needs about 2.5 to 3 pixels per module of the QR code. With 50 mm markers that is at least about 1.25 to 1.5 pixels per millimetre, so at an image width of 1280 pixels a work surface of at most about 850 to 1000 mm. Below that the dialog warns. Then these help: get closer, a higher resolution, larger markers. Small, noisy markers are increasingly **no longer read** in the test.
* **Camera moved:** The calibration holds for one camera position and one image size. If the camera is knocked, you have to calibrate again. The program does **not** detect a moved camera.
* **Not available:** live image in the drawing area, live machine image with tool position, streaming from a phone, automatic reaction to the image, several cameras.

## Windows camera permission and privacy

Desktop programs only see the camera if, under **Settings → Privacy & security → Camera**, **Camera access**, “Let apps access your camera” and below it “Let desktop apps access your camera” are switched on. If Windows denies access, the dialog explains exactly this path. All of this is **not checked under Windows**.

**Nothing is saved or transmitted**: single frames go only to the program on your computer and stay in working memory. No history, no still images on the disk, no cloud, no portal. The camera can capture people. Do not point it at other people’s rooms.

## When markers are not found

See [Troubleshooting](Troubleshooting), section “The camera does not find the markers”.

## More

* The drawing area and working with shapes: [Drawing and importing](Drawing-and-Importing)
* A report on your test with a real camera: [Contributing and testing](Contributing-and-Testing). That helps especially.
