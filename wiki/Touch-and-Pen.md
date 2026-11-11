**English** | [Deutsch](Touch-und-Stift)

# Touch and Pen

ortino.CAM can be used with a **finger and a pen**, on a tablet (portrait too; the window may be as narrow as 760 px) or a touch laptop. With a mouse and keyboard everything stays as it was.

> **Honest about the status:** Touch and pen operation was **checked only with the touch emulation of Chromium**. Never on a real touch device, never under Windows (WebView2), never with a real pen and never on a real machine. The behaviour of the Windows on-screen keyboard and of the system gesture “press and hold” is unchecked.

## Switching it on

*Settings ▸ Appearance & language ▸ Touch control*: **Automatic** (the first touch switches the mode on, a mouse click switches it off again), **On** or **Off**. The setting stays on this computer and is not part of the backup in the portal.

## In the drawing area

| Gesture | Effect |
|---|---|
| Tap | select |
| Drag with one finger | depends on the tool (draw, move, selection frame) – only after about 10 px, so that a tremor triggers nothing |
| Double tap | like a double click |
| Long press | context menu (in lists too, for example for the operations: “Move up/down”) |
| Two fingers | pinch zooms, moving together pans the view; an input that has begun is taken back |

A bar below the drawing area offers **Done, Cancel, Delete, Undo, Redo**, plus Shift and Hand. The pen behaves like the mouse. Controls are at least 44 × 44 px, number fields open the number keyboard (fields with a formula the text keyboard), and hints appear on long press instead of only on hover.

## At the machine: safety comes first

* All confirmation questions and locks stay (start check, “Move here”, work zero, homing, spindle, probing).
* A button only fires if **the same finger presses and lifts on the same button**; several touches and dragging away trigger nothing.
* **No continuous jogging by finger or pen** by holding. Jogging works in steps.
* On the machine card, pinch and pan **never** set a target, only a tap does.
* Start and Stop are large (64–68 px), and Stop is always inside the window. A finger resting on the screen only locks the machine buttons; there is no palm detection.

## Not built

Reordering the operations by dragging with a finger (the long-press menu has “Move up/down”), formulas on the number keyboard, pen pressure and tilt, pinch for the 3D views and for the cabinet and production drawing areas.

## Next

* [Keyboard Shortcuts](Keyboard-Shortcuts)
* [Milling on the Machine](Milling-on-the-Machine)
* [Troubleshooting](Troubleshooting)
