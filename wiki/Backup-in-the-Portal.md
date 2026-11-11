**English** | [Deutsch](Sicherung-im-Portal)

# Backup in the portal

With an account in the community portal you can back up **machine profiles**, your **own bits** (“My library”) and a fixed selection of the **program settings** privately and retrieve them later on the same or another computer: after a reinstallation, or to keep office and workshop in step, for example. **None of this happens by itself**: only what you trigger in the dialog is backed up and retrieved.

> **Honest about the status (from version 0.3.12):** The backup is checked against a **real portal server** with a database, with the simulator and in the browser (Chromium) with two programs that play office and workshop. **Not yet** against the portal on the internet and **not under Windows** (WebView2, credential storage). You need a portal from version 0.3.12; for an older one the program says so and does not offer the backup. Everything else works as before.

## Opening

Menu **Settings ▸ Backup in the portal …**, in the community the card *Backup in the portal …* on the page *Account*, or the command palette (`Ctrl+K`, “Backup”). At the top, the dialog shows which portal you are signed in to and as whom. If no portal has been set up yet or you are not signed in, it leads you to the sign-in (see [Community Portal](Community-Portal-en)).

## Backing up

1. Tick what is to be backed up: *Machine profiles* (only your **own**, not the bundled templates), *My cutters*, *Settings*.
2. Click **Back up**. For each ticked kind a new version is created in the portal; up to **10 versions per kind** are kept, then the newest displaces the oldest.
3. Afterwards each kind shows its result (“backed up”, “nothing to back up” or an error with a fix). A kind that fails does not hold up the others.

## Retrieving: preview first

**Retrieve** changes nothing at first but shows a **preview**. You choose the **version** (the newest, an older one or a local copy from replacing) and the way of applying it:

| Choice | What happens |
|---|---|
| **Merge** (default) | Only **new things** are added. What exists here stays; duplicates are skipped; an existing but differing profile is **never** silently overwritten. |
| **Replace** | What you have here becomes the same as what is in the portal. The program asks explicitly, names what is removed and replaced, and automatically makes a **local copy** **beforehand**, which you can go back to. |

The preview lists every entry individually: **new**, **already identical**, **exists but differs**, **invalid** (never applied, with the reason). For the *Settings* you see a **list of differences** in plain words (value here, value in the portal); every setting can be deselected. When merging, only settings that are still at their default here are applied. Several kinds at once are applied in a fixed order: first machine profiles, then cutters, last settings, so that a default machine from the settings already exists.

In the box *Backed-up versions in the portal* every version can be **deleted** individually (with a confirmation).

## What is backed up, and what never is

* **Machine profiles:** name, travel limits, spindle and feed rate limits, accessories, probe, calibrations and height map of the spoilboard, notes, without paths and connection data.
* **My cutters:** dimensions, cutting values, notes of your own library (not the bundled catalogue).
* **Settings:** only a **fixed list** of 22 settings, for example appearance, language, snapping, notifications, default machine, Z zero of new projects. A new setting of the program stays out by itself until somebody deliberately includes it.
* **Never backed up:** tokens, keys and passwords (including the assistant’s API key and the portal sign-in), connection data (ports, addresses, camera), file paths and shared folders, recently opened files, window size and layout, computer identifiers, logs.

The backup is **private in your account**; other accounts do not see it. But it is **unencrypted in the portal’s database**, like all account data, and the operator technically has access to it. Encrypting with your own key, automatic backup and sharing a backup with a second account do not exist. Limits: 4 MiB per version, 64 MiB per account, at most 30 creations or deletions per hour. If you delete your account, the backups are deleted too; the portal’s privacy policy mentions them.

## If it does not work

| Message | What you can do |
|---|---|
| The portal is too old / the backup is not offered | The portal must run version 0.3.12 or newer. The operator has to update the server. |
| Not signed in | Sign in in the dialog (device sign-in as in the community). |
| “All backups of the account together are too large” | Delete versions you no longer need in the dialog and back up again. |
| “Too large” | One version exceeds 4 MiB (many machines with height maps): remove profiles or bits you do not need. |
| “Too many requests” | Wait for the stated time. |

## Next

* [Setting up the machine](Setting-Up-the-Machine) (profiles, list, default machine, “My machine”)
* [Tools and cutting data](Tools-and-Cutting-Data) (My library)
* [Community Portal](Community-Portal-en)
