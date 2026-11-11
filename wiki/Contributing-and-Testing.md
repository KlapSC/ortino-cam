**English** | [Deutsch](Mitmachen-und-Tests)

# Contributing and testing

**New contributors are welcome.** The source code of ortino.CAM is not public, but you can still take part in many ways. Most valuable are **tests on real machines**, because ortino.CAM is built for the most part with Claude Code (Anthropic) as co-author. Thousands of automatic tests check the calculations, but they come from the same source as the code. Only a test on a real machine shows whether something really works.

The detailed rules are in the [CONTRIBUTING.md](https://github.com/KlapSC/ortino-cam/blob/main/CONTRIBUTING.md). Questions, bugs, wishes and machine reports go through **[GitHub Issues](https://github.com/KlapSC/ortino-cam/issues/new/choose)**. Issues are public: do not put any personal data in them. Privacy requests and legal matters about the community portal go to the e-mail address in the [portal's imprint](https://ortino-cam.com/imprint).

Note: The issue templates and the CONTRIBUTING.md are in German. Below, the template names and field names are given in English translation, with the German name where it helps you find the template.

## What is welcome

| Contribution | How |
|---|---|
| **Test on a real machine** (most valuable) | Issue template “Test an einer echten Maschine” (test on a real machine). Failures help too. |
| **Bug report** | Issue template “Fehler” (bug) |
| **Question** | Issue template “Frage” (question) |
| **Wish** | Issue template “Wunsch” (wish). Describe which problem you want to solve, not only which function you imagine. |
| **Machine profile** | Export it from the program and submit it as a pull request |
| **Post-processor template** | TOML and Jinja as a pull request |
| **Example project** | `.ocam` file as a pull request |
| **Translations and guides** | Corrections and new texts as a pull request. You report errors in the wiki as an issue. |
| **Working on the program** | Issue with the title “Mitarbeit am Programm” (working on the program) |

**Milling designs** (signs, furniture, patterns …) do not belong here but in the [community portal](Community-Portal-en). It is best to share them directly from the program.

## How to report a test on a real machine

Please test **first without a tool and without material**, with the emergency stop within reach and with the notes from [Milling on the machine](Milling-on-the-Machine). Then:

1. Open a new issue and choose the template **“Test an einer echten Maschine”** (test on a real machine).
2. Fill in the fields:
   * **Version of ortino.CAM** (in the dialog “About ortino.CAM”),
   * **Machine and controller** with firmware, for example “Ultimate Bee 1000, CNC xPRO V5, GRBL 1.1h”,
   * **What did you test?** The choices are: fixed probe (measure tool, change assistant), zeroing the spoilboard and height map, touch plate and corner block (probing), change assistant with length sensor, phone remote control, move to position, machine profile, or other,
   * **Result:** worked as described, works with limitations, did not work, or the machine reacted unexpectedly,
   * **What happened?** Describe the procedure and the messages of the start check, and paste an excerpt of the machine's **console** (in the step “Cut” the card “Console”, the lines with `tx` and `rx`).
3. **No personal data**: no names, addresses, serial numbers and no login credentials in reports, projects or pictures.

A report in which **nothing worked** helps too. A report that something worked helps just as much, because that is how “only checked against the simulator” eventually becomes “tested”.

### What is especially needed

Only on the **Ultimate Bee with xPRO V5** have these been tested so far: pockets, V-carving, contours, homing and tool change with the touch plate (version 0.3.3); in addition, according to the operator, on the phone remote control stop, jogging and setting work zeros, and with version 0.12.0 a single run of about one hour (pocket and contour in birch, without pause, feed override or tool change; according to the operator the live animation matched the milling “perfectly”). Everything that follows is **only checked against the simulator, tests or generated pictures** and is waiting for your report:

* fixed probe, measurement of the spoilboard and height map,
* phone remote control: pause, resume and the display of position and progress, other phones and browsers (stop, jogging and setting work zeros are confirmed on a real machine according to the operator),
* “move to position”, change assistant with length sensor, probing with the corner block, dust extraction,
* running the frame, air cut, pause and start from line (not confirmed individually on the real machine),
* thread milling, maintenance plan and tool life limits,
* the camera on the worktable (with a real camera),
* the new post-processors (UCCNC, Centroid, ShopBot, MASSO, PlanetCNC) and controllers other than the xPRO V5,
* milled fits, finger joints, inlays, reliefs and furniture parts,
* runs **with pause, feed override (overrides) and a tool change in the middle of the program**, in materials other than birch and with other machines,
* parts from the [Creators](Creators) (since 0.13.0; advent calendar, wreath, lantern and garland since 0.14.0): box, gears, puzzle and the others have **never been milled or glued**; please try them on an offcut first and with the fit test coupon. For the lantern: use an LED tealight; the creator does not check whether an open flame is safe,
* hole patterns from the Pattern Studio (40 kinds, 80 templates, of which the word and logo collage since 0.16.0), the new relief templates (62) and the wall art motifs of the Art Designer (14), extended since 0.14.0 and 0.16.0: **never milled**; reports on fine webs (fish scales, shippo, spirals) and thin points (ogee, snowflakes, maple leaf, stars) in real wood are especially wanted; for the word and logo collage (webs of about 1 mm between letters, islands with bridges, small parts) and for the logo from your own file,
* **custom templates** on Windows (WebView2): do they remain after a restart and after an update, does “Save as file” show a save dialog, does dropping files onto the category “Own” work? Also **SVG and DXF files from the [online generator](Shape-and-Pattern-Generator)** in other CAM software and on a machine (so far only reading them back into ortino.CAM has been checked) and the **“Optimised”** cutting plan in the [Furniture Designer](Furniture-Designer) on a real saw (so far only measured on the computer),
* the **examples** of the gallery, milled in an offcut (**not milled**), and whether the **lessons** fit your experience,
* **Bézier curves from real Illustrator, Inkscape or CorelDRAW files** (so far only checked with self-generated SVG and PDF files) and serial numbers on milled parts.

## Contributions as files (pull request)

For files you open a **pull request** in the [public repository](https://github.com/KlapSC/ortino-cam). One change per pull request, with a short description.

* **Machine profile:** In the program under “Machines”, choose the profile and **Export**. The file must contain **no height map and no personal notes**. Put it under `maschinenprofile/`, file name `hersteller-modell-steuerung.json` (manufacturer-model-controller; for example `ultimate-bee-1000-xpro-v5.json`). In the pull request, state the source of the dimensions and whether you use the machine yourself. Only machines that you use yourself or know well.
* **Post-processor template:** TOML and Jinja under `postprozessoren/`, with one sentence on **which controller and firmware you tested it on** and how (on the machine, or only the output checked). See [Post-processors and controllers](Post-Processors-and-Controllers).
* **Example projects:** `.ocam` files under `beispiele/`, your own work, small (under 1 MB), with one line on what they show.

### Rules and rights

* Only **your own work** or material you may pass on. No files from other people's catalogues, no price lists, no third-party data without permission.
* **No personal data** in projects, profiles and pictures.
* Stay friendly. Anyone who insults or harasses others is excluded from issues and pull requests.
* With a pull request you confirm that the contribution is yours, and you grant the operator a simple, temporally and geographically unlimited, royalty-free right to use it, modify it and pass it on with ortino.CAM (also in the closed program version and in the portal). Your authorship stays with you, and you may continue to use your contribution yourself. The wording in the CONTRIBUTING.md is authoritative.

## Working on the program

If you would like to work on the program itself, write an issue with the title **“Mitarbeit am Programm”** (working on the program). Briefly describe what you are interested in and what experience you bring (Rust, TypeScript and React, CAM, GRBL, testing, documentation). The operator gives interested people access to the private development repository and discusses task, way of working and rights with you before you start. Whoever gets access treats the source code as confidential.

## Security vulnerabilities

Do **not** report security vulnerabilities as a public issue. In the **Security** tab of the repository there is “Report a vulnerability” (a private report to the operator). Particularly important are vulnerabilities in the phone remote control, the updater, the machine connection and the processing of other people's files. If a bug can cause the machine to move unexpectedly, report it **urgently** and describe the conditions. More in the [security policy](https://github.com/KlapSC/ortino-cam/blob/main/SECURITY.md).

## In short

ortino.CAM is closed source, but you can still help in many ways. The most valuable contribution is a **test report from a real machine**, including failures. Use the issue template "Test an einer echten Maschine" (test on a real machine), and test without tool and material first, with the emergency stop within reach. Machine profiles, post-processor templates, example projects, translations and guides are welcome as pull requests with data files only (see the CONTRIBUTING.md in the repository). Milling designs belong in the community portal. Questions and bugs go through GitHub issues (public, so no personal data); data protection requests and legal matters about the portal go to the e-mail address in the [portal's imprint](https://ortino-cam.com/imprint). The software is provided as is, without warranty.
