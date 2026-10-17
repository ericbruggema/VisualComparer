# Libraries and settings

[← Back to the overview](../README.md)

## Libraries

A **library** keeps a set of folders together with its mode, accuracy and sensitivity, and its saved results. Use one library per purpose, for example *Family photos*, *Holiday 2024*, *Downloads* or *Work videos*.

At the top of the window you choose the active library; next to it are **＋ New library…** and **⚙ Manage libraries…**. The management screen lists all libraries with their last scan and the total space you could free, and lets you open, rename, duplicate, export (as a `.vcslib` file), import and delete them.

* **Results are saved per library**: the groups, what you already ticked and where you were. See [Results and clean-up](results-and-cleanup.md#saved-results).
* **Continue where you were**: close the program (or let it crash) and the results come back at the next start.
* **Switching** is possible at any time except during a scan. If you cancel a new scan, the earlier saved results of that library come back.
* **Compare two libraries with each other**: select two in the management screen (`Ctrl`+click) and choose *Compare the 2 selected*. A new library (A against B) is made, and what was already scanned does not have to be scanned again.
* Protected folders and the keep rules are global (Settings).

## Scan modes

| Mode | Meaning |
|---|---|
| **All vs all** | Duplicates within all chosen folders. |
| **Folder A vs folder B** | Only copies between the two sets are reported, not copies inside one set. Handy to check what of an old backup is also in a new one. |
| **New vs library** | New files are compared against everything that was scanned earlier (or against one chosen library). Files from earlier scans come from the cache, so this is fast. |

## Compare again with another sensitivity

On the results screen, **Sensitivity…** lets you compare again from the cache without scanning the folders. See [Results and clean-up](results-and-cleanup.md#compare-again-with-another-sensitivity).

## Settings

Open **Settings…** at the top of the window. Changes apply after **OK**.

### Scan

| Setting | What it does |
|---|---|
| **Include subfolders** | Search folders recursively (on by default). |
| **Include network drives (can be slow)** | Network and external drives are skipped by default. |
| **Ignore files smaller than … MB and shorter than … seconds** | Filters for **videos** (tiny or very short clips). Photos are always searched. |
| **Number of videos analysed at the same time** | *Automatic* = half of your processor cores (4 to 8 with an NVIDIA graphics card). If your GPU or processor is not fully used yet, try more (for example 10–16); a slow disk or network drive remains the limiting factor. |
| **Video file types** / **Photo file types** | The extensions that are searched, separated by commas. |
| **How photos are read** | Built-in Windows reader first, ffmpeg if that fails *(recommended)* · built-in reader only · ffmpeg only. See [Photos](photos.md#how-photos-are-read). |
| **Exclusion patterns** | One per line; `*` and `?` are wildcards, for example `*\Thumbs\*`, `*.part`, `*\$RECYCLE.BIN\*`. |

### Compare

| Setting | What it does |
|---|---|
| **Compare resolution** | Videos are always read over their full length. When two videos are aligned, the number of points compared per video is capped, because memory and time grow quadratically. A higher limit gives a more accurate alignment of long videos but costs memory and time. *Automatic* adapts to your memory and processor. A calculator shows the memory and the expected time (**Measure my computer** runs a short test). |
| **Align on the graphics card (GPU)** | Optional, off by default. Uses DirectX 12, so it also works with non-NVIDIA cards, and gives exactly the same result as the processor. If anything goes wrong the program falls back to the processor. |

### Cache

Fingerprints of previously scanned files are reused, so that the next scan of the same files is much faster. **Clear cache** removes them (the next scan then analyses everything again). The tab also shows how many files are in the database and where your data folder is.

### What to keep?

The criteria that choose the best file of a group, applied from top to bottom. Tick what counts and reorder with the arrows: highest resolution, longest duration, highest bitrate, preferred folder wins, newest file, oldest file, preferred codec. Set your **preferred folders** (the first wins) and **preferred codecs** here too.

### Safety

| Setting | What it does |
|---|---|
| **Protected reference folders** | Files in them are never deleted and count as the original. |
| **Quarantine folder** | Where quarantined files go. Empty = `data\quarantine` next to the program. |
| **Extended check before deleting** | Reads and compares both files again just before they are removed (slow, especially over a network drive). The quick check (the files still exist and are unchanged) is always done. |

### Appearance

| Setting | What it does |
|---|---|
| **Language** | Automatic (Windows language), English, Dutch or German. Takes effect after a restart. Another language? Put a `.json` file in the `lang` folder next to the program (see [Installation](installation.md#language)). |
| **Theme** | Follow Windows, light or dark. |
| **Size of the thumbnails in the timeline** / **Number of thumbnails per video** | How big and how many frames the film strip shows. |

### About

Shows the version and the limits of the free edition, a link to the project page and the terms of use.

## Files and folders the program uses

| What | Where |
|---|---|
| Settings | `data\settings.json` (an unreadable file is set aside as `settings.json.bad`) |
| Libraries, saved results | `data\libraries.json`, `data\results\` |
| Fingerprint cache and action log | `data\videocomparer.db` |
| Quarantine | `data\quarantine` unless you choose another folder |
| Crash log | `crash.log` next to the program, or in the data folder |

See [Installation](installation.md#where-is-my-data) for where the data folder is.
