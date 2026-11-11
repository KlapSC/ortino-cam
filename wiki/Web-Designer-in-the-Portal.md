**English** | [Deutsch](Web-Designer-im-Portal)

# Web Designer in the portal (kitchen and furniture in the browser)

Since version 0.5.0 the **Kitchen Designer** and the **Furniture Designer** also run in the [community portal](Community-Portal-en): in the browser, without installing the program. You design, see the result in 3D, get a parts list and a cutting plan, save the design in your account and download it as a file to keep working on it in the program and mill it.

> **Honest about the status:** The Web Designer is new and **only checked against tests and in Chromium**: not by several people at the same time, not on the operator’s server under load, not in Firefox, Safari or phone browsers, not with a real mail server. **Nothing from the designers was milled or built** (see [Furniture Designer](Furniture-Designer) and [Sheets and furniture](Sheets-and-Furniture)). A design is planning, not proof.

## Opening it

1. Sign in to the portal. You need an account with a **confirmed email address** (the server only calculates for confirmed accounts; the mail with the confirmation link arrives when you register, and under *Account* you can request it again).
2. Click **“Design a kitchen or furniture”**: in the navigation (where the link is called “Kitchen & furniture”), in the account menu or on the start page. The designer lives at the address `/designer/` of the portal. Without signing in it leads you to the sign-in and back afterwards.
3. At the top choose between **Kitchen** and **Furniture**. Operation is the same as in the program: the list on the left, 3D preview and floor plan in the middle, the fields of the selected part on the right; undo (Ctrl+Z) and redo (Ctrl+Y), German and English, light and dark.

What applies in the program applies here too: [Furniture Designer](Furniture-Designer), [Kitchen rendering](Kitchen-Rendering) and [Sheets and furniture](Sheets-and-Furniture).

## Saving, opening, downloading

* **Save** (Ctrl+S) stores the design **privately in your account**. The first time, the designer asks for a name (suggestion with the date); after that Ctrl+S saves without asking. *Save as new design …* makes a copy. The header shows **New**, **Saved** or **Unsaved**; when you close the tab, the browser warns about unsaved changes.
* **Open** (Ctrl+O) shows your designs with type (kitchen, furniture, both), size and date. There you can also **rename, download and delete** them.
* **Limits:** at most **30 designs**, **40 MB** together, **8 MB** per design (the operator of the portal can change this). The display shows how much is used.
* **Download (.ocam)** gives the project file that the program also opens. In the program you then find *Create parts & prepare milling*, the machine and everything else. Conversely, you can open an `.ocam` from the program in the Web Designer (**Open file**, up to 8 MB).
* **Interim state:** Your browser stores an interim state every 20 seconds as long as there are unsaved changes. If the session on the server expires, the designer offers to restore it. **This does not replace saving**; save regularly.

## Sharing designs and editing in turns (since 0.6.0)

You can share a saved design with other accounts, for example with a colleague or for a customer’s approval.

* **Inviting:** In the designer choose *Share …* and enter the **username** of an existing account (not the email address). You set the role: **View** or **Edit**. The invited person gets a notification in the portal (bell, page *Account → My shares*) and accepts or declines. After a decline you cannot invite the same person again for 30 days; anyone who no longer wants to hear from someone can **block** invitations from an account.
* **Editing in turns:** Only **one person** writes at a time. Whoever chooses *Take over editing* holds the lock (it expires after two minutes without a sign of life; after ten minutes without a change it counts as dormant and can be taken over). Everyone else sees the **saved version** in read-only view mode and can **ask** for the hand-over. A chip display says who is editing right now.
* **Conflicts:** Saving is done against the version you opened. If someone else has saved in the meantime, ortino.CAM **overwrites nothing silently** but shows a conflict dialog: you save your version as a **copy** in your account or download it.
* **Viewers** may **download** the design and **save a copy in their own account**. They cannot change it.
* **View link** (for example for customers): one link per design, which you can delete or replace at any time. It only works for **signed-in** accounts with a confirmed address and expires after 90 days at the most. The key is in the part of the address after the `#` and does not go to proxies; the server only knows a check value.
* **Deleting:** If the owner deletes the design or their account, the design is **gone for everyone**. Members can leave on their own at any time. A shared design counts towards the storage space of the owner only.
* **Not included:** simultaneous live editing, comments, chat, version history.
* **Honest about the status:** Never used by several real people, only checked in Chromium and with tests. If two people work in the same account in two tabs, they still share one calculation; if you open a different design in the second tab and save in the first, you get a message instead of an overwrite.

## Editing at the same time (live, since 0.7.0)

For a design that he has shared with at least one person, the **owner** can switch on **live editing**. Up to four people then work **at the same time** on one shared calculation on the server: changes appear for everyone after a few hundred milliseconds, and you see who is there and what is currently selected. Saving is automatic and with a version check; **Undo** only takes back your own last change. Without this permission it stays with editing in turns with a lock. There are only **a few live places** (default: two live sessions at the same time, at most four hours per session); if none is free, it stays with editing in turns. **Limits:** never used by several real people at the same time, runs on only one server instance.

## What the web version does not have

Milling, the machine, G-code, the program’s settings, file access, custom building blocks and custom fittings (you can choose the bundled ones), *Create parts & prepare milling*, Claude/MCP and the camera. Parts list (as CSV or HTML), cutting plan, rendering, checklist, variants, customer sheet, patterns and reliefs are there. Where a button is missing, a note says to download the design and keep working on it in the program.

## Good to know

* **The server calculates.** The calculation does not run in your browser but on the portal’s server, in a sealed-off environment per user (without access to files, serial, network). Nothing works without a connection to the portal.
* **Session:** The server keeps your calculation for at most **60 minutes without a call**; after a restart of the server (update) it is gone. Then the last saved design (or your browser’s interim state) applies.
* **One design at a time:** All tabs and devices of your account share the same calculation. Do not work in two tabs at the same time (if one tab opens a different design, saving in the other tab is refused instead of overwriting).
* **Too busy:** If the server is already calculating for many others, you get “The server is busy right now”. Wait a moment and try again.
* **Privacy:** Your designs are in the portal’s database, visible only to your account. The designer sets a cookie that ties your browser to your session. What else the portal stores is in its privacy policy.

## For operators of their own portal

In the portal’s administration the **“Web designer”** card shows state, load, counters since the start, the size of all designs (without names and contents) and recommendations, for example when to change the number of simultaneous calculations. Shared designs need the server image 0.6.0 (migration 7).

The Web Designer needs the **server image 0.5.0** (the program alone is not enough). Defaults and switches (`ORTINO_HUB_DESIGNER_*`: simultaneous calculations, time limits, sizes, designs per account; switch off with `ORTINO_HUB_DESIGNER=off`) are in the portal’s operating manual in the source code repository. **On a NAS with 2–4 cores** lower the number of simultaneous calculations to the number of cores; the load is not measured. Calculation is done **only for accounts with a confirmed email address**: without set-up mail sending (SMTP), nobody can use the Web Designer.

## Troubleshooting

| Symptom | Fix |
|---|---|
| “Please confirm your email address first” | Click the link in the confirmation mail or request a new mail under *Account*, then reload the designer. |
| “The session has expired” | Open the last saved design or restore the interim state. |
| “The server is busy right now” | Wait a moment, then try again. |
| “This function is not available in the web designer” | Download the design (.ocam) and keep working on it in the program. |
| “The space for designs in your account is full” | Under *Open*, download and delete old designs. |
| There is no entry in the portal | The operator has not switched on the Web Designer or the portal is not yet on version 0.5.0. |
