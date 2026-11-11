**English** | [Deutsch](Tastenkürzel)

# Keyboard shortcuts

This page lists the keyboard shortcuts of ortino.CAM under Windows. In the program, the `?` key (`Shift+ß` on a German keyboard) or Help → “Keyboard shortcuts” shows the current list. The command palette (`Ctrl+K`) finds **every** command by keyword and shows its shortcut. Some shortcuts only work in the matching step, as long as you are not typing in a text field.

> The assignment is fixed. There are no freely assignable shortcuts in this version.

## Everywhere

| Shortcut | Effect |
|---|---|
| `Ctrl+K` | command palette |
| `?` | show keyboard shortcuts |
| `Alt+1` to `Alt+5` | go to the step Project, Design, Machining, Check, Cut |
| `Alt+Home` | go to the start page with the quick access tiles (since 0.13.0; not yet tested under Windows, the Home button in the header bar and the command palette work in any case) |
| `Ctrl+N` | new project |
| `Ctrl+O` | open project |
| `Ctrl+S` | save |
| `Ctrl+Shift+S` | save as |
| `Ctrl+I` | import file (SVG, DXF, PDF/AI, image) |
| `Ctrl+Z` | undo |
| `Ctrl+Y` or `Ctrl+Shift+Z` | redo |
| `Ctrl+B` | show and hide the sidebar |
| `Ctrl+J` | show and hide the properties panel |
| `Ctrl+Shift+D` | open the community portal |
| `Ctrl+Shift+M` | furniture and kitchen |
| `Ctrl+L` | open the assistant |
| `Ctrl+Shift+L` | “Ask Claude about this view” |

## Design: tools

| Key | Tool |
|---|---|
| `V` | Select |
| `A` | Edit nodes |
| `R` | Rectangle |
| `E` | Ellipse and circle |
| `P` | Polygon (`S` switches to star, digits 3 to 32 or `↑`/`↓` set the number of corners) |
| `L` | Line and polyline |
| `B` | Pen (Bézier curves) |
| `Shift+B` | Freehand |
| `T` | Text |
| `M` | Measure |
| `O` | Round corners |
| `H` | Chamfer |
| `X` | Trim |
| `N` | Extend |
| `Esc` | cancel input, then switch to Select, then clear the selection |

## Design: editing and view

| Shortcut | Effect |
|---|---|
| `Ctrl+A` | select all |
| `Ctrl+C`, `Ctrl+V` | copy, paste |
| `Ctrl+D` | duplicate |
| `Del` | delete |
| `Shift+H`, `Shift+V` | flip horizontally, vertically |
| arrow keys | move the selection by one grid step (tenfold with `Shift`) |
| `F` or `Home` | fit the view |
| `Z` | zoom to the selection |
| mouse wheel | zoom |
| drag with the middle mouse button, or hold `Space` and drag | pan the view |

## Nodes, pen and freehand

| Shortcut | Effect |
|---|---|
| `Tab`, `Shift+Tab` | next, previous node |
| `Ins` or `+` | insert a node in the middle of the selected segments |
| `Del` | delete the node, keeping the shape where possible |
| `Ctrl+Del` | delete the node without keeping the shape |
| `Shift+C`, `Shift+S`, `Shift+Y` | node type: corner, smooth, symmetric |
| `Shift+L`, `Shift+A`, `Shift+U` | segment type: line, arc, curve |
| `Shift+J` | join end nodes, close an open path |
| `Shift+X` | split at the selected nodes |
| `Shift+R` | reverse direction |
| `Shift+T` | set the plunge point (the toolpath starts there) |
| arrow keys | move the selected nodes (tenfold with `Shift`, one tenth with `Alt`) |
| Pen: `Backspace` | take back the last node |
| Pen: `Enter`, double-click or `Esc` | finish the line |
| Pen: `Shift` while dragging | snap the angle in 15° steps |

## Checking and milling

| Shortcut | Effect |
|---|---|
| `Space` (in the Check step) | play or pause the simulation |
| arrow keys (“Manual control” card, with the “Keyboard” switch on or when the focus is in the card) | jog X and Y |
| `Page Up`, `Page Down` | jog Z |
| `Shift` | tenfold step size |

> In the Cut step these keys move the **real machine**. Switch on the “Keyboard” switch only when you need it, and keep the emergency stop within reach.

## In dialogs and studios

| Shortcut | Effect |
|---|---|
| `Ctrl+Enter` | insert or apply (Trace image, Pattern Studio, Relief Studio, Fit assistant, Joints, template form) |
| `Esc` | close the dialog or discard the input (with unsaved input the program asks) |
| `Ctrl+Enter` in the Creator (since 0.13.0) | create the workpiece in the project |
| arrow keys in the Creator gallery (since 0.13.0) | choose a creator; `Esc` clears the search |
| arrow keys in the Pattern Studio | change the template card |
| `Esc` in the search field of the Pattern Studio (since 0.14.0) | clear the search |
| `+`, `-`, `0` in the Pattern Studio | zoom, fit to the sheet |

## Furniture and kitchen

| Shortcut | Effect |
|---|---|
| `O` | open and close doors |
| `E` | exploded view |
| `M` | show dimensions |
| `B` | show holes |
| `C` | colour parts by cabinet |
| `V` | show true colours (chosen colours and gloss levels) |
| `R` | export rendering (image of the kitchen) |
| `G` | material and sheets of the kitchen |
| `K` | kitchen (uniform settings) |
| `N` | new base cabinet |
| `2`, `3` | parts list, cutting plan |
| `↑`, `↓` | select a cabinet |
| `Alt+←`, `Alt+→` | move the cabinet |
| `Del` | delete |
| `Ctrl+D` | duplicate |
| `Ctrl+S`, `Ctrl+Shift+S`, `Ctrl+O` | save the kitchen, save as, open |
| `Ctrl+C`, `Ctrl+V` | copy, paste the selected cabinets (also into another project) |
| `Esc` | close |

In the **Furniture** area the same keys apply for selection, `N` (new piece of the chosen type), `Del`, `K` (overview), `R` and `Ctrl+Z`/`Ctrl+Y`; pieces are dragged in the floor plan, see [Furniture Designer](Furniture-Designer).

## Cutter library

| Shortcut | Effect |
|---|---|
| `/` | search |
| `Enter` | details |
| `Space` | compare |
| `F` | favourite |
| `A` | add to the project |
| `Esc` | close |

Further notes, such as `Ctrl+Z` after actions by Claude or the assistant, are on the respective pages: [Drawing and importing](Drawing-and-Importing), [Milling on the machine](Milling-on-the-Machine) and [Sheets and furniture](Sheets-and-Furniture).
