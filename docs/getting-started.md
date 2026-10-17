# Getting started

[← Back to the overview](../README.md)

This page walks through your first scan. Four steps: **pick folders, scan, read the results, clean up.** Everything shown here is the real program, scanning a small archive of free-to-use photos and videos.

The program has three screens; the step bar at the top (**1 Start › 2 Scan › 3 Results**) shows where you are.

## Before you begin

* Install or unzip the program, see [Installation](installation.md).
* The first time you start it you are asked to read and accept the terms of use. A short, interactive guide follows with five pages: what the program does, how a scan runs, how to read the results, how to clean up safely and why it is different. You can open it again at any time with the **? Guide** button at the top.
* If you want to try it first, use a small folder. The free edition handles up to 500 videos and 2,500 photos per scan.

## 1 · Start: pick what to scan

<p align="center"><img src="images/windows-start.png" alt="The start screen with four cards" width="820"></p>

The start screen has four cards.

### Card 1 · Folders and files

Drag folders (or single files) onto the window, or use **＋ Folder…** and **＋ File…**. Remove one with ✕ or empty the list with **Clear all**. Under the list you see at once how many files were found and their total size.

When you add a folder you are asked whether to also add all its **subfolders** to the list separately. Say yes if you later want to remove one subfolder without losing the whole folder. For a very large archive the program searches the subfolders in a progress window with a counter that you can cancel.

### Card 2 · What to compare

| Choice | Use it when |
|---|---|
| **All vs all** | You want duplicates within all the chosen folders. The default. |
| **Folder A vs folder B** | You only want to know what is in the old backup that is also in the new one. Only copies *between* the two sets are reported, not copies inside one set. |
| **New vs library** | You just imported or backed up new files and want to check them against everything you have scanned before. Fast, because earlier files come from the cache. You can compare against everything ever scanned, or against one library. |

### Card 3 · What to look for

* **Videos and photos**: duplicate videos and duplicate photos, in separate groups.
* **Videos only**: ignore all photos.
* **Photos only**: JPG, PNG, WebP, HEIC and more. Finds the same photo in another size or format.

### Card 4 · Accuracy

Photos on the left, videos on the right (or one of the two over the full width when you only scan one kind).

* **How strict for photos**: five levels, see [Photos](photos.md). *Same picture* is a good start. *Also rotated or mirrored* is on by default; switch on *Also cropped* if you expect cut-down versions.
* **How accurate for videos**: *Fast*, *Normal* or *Thorough*, see [Videos](videos.md). Leave **Use CUDA (NVDEC)** on if you have an NVIDIA graphics card.
* **More options** has the sensitivity and a button to all settings (filters, exclusion patterns, keep rules, quarantine folder, protected folders).

Press **Start scan**. At the bottom you see a summary of the previous scan.

## 2 · Scan: watch it work

<p align="center"><img src="images/windows-scanning.png" alt="The scanning screen with phases and live numbers" width="820"></p>

You see each phase live: **Finding files › Analysing › Finding candidates › Comparing › Grouping**. Each finished phase keeps its final numbers in the phase bar. Below you see the percentage, the time left, the speed and one card per phase with statistics: files found, how many come from the cache and how many are new, whether the GPU or the processor does the work, how many candidate pairs there are and how many were smartly excluded, how many matches were found.

* Finished phases collapse into one line; click a heading to open it again, or tick **Show all details**.
* **Cancel** works at any time. What is already analysed stays in the cache, so the next scan continues where you stopped.
* A first scan of a large archive takes a while, because every photo and video is analysed once. Later scans only analyse new or changed files.

## 3 · Results: read the groups

<p align="center"><img src="images/windows-results-photos.png" alt="A group of photos with the reason for every match" width="820"></p>

All groups are listed below each other; the selected group is open. Each row is one file with a switch (✓ keep / 🗑 remove), its properties and the reason it matched.

* **The best version is marked** and kept by default. "Best" follows your keep rules: highest resolution first, then longest, best bitrate, preferred folder, newest or oldest, preferred codec. For photos the highest resolution wins, then the largest file (usually the least compressed).
* **Photos**: each copy says why it matched, for example "smaller: 1200×900 · other format: BMP" or "rotated 270°".
* **Videos**: a bar on a shared timeline shows which part of each copy matches the best version. A clip that is part of a longer video only fills part of the bar. Click or drag on a bar and every copy jumps to the same scene. Next to the bar you see the percentage and how many frames and seconds match.
* Labels: **identical** (byte for byte the same, verified with SHA-256), **same picture** (a different file with a 100% identical picture) and **same size** (a suspicion until the check has finished).

<p align="center"><img src="images/windows-results-videos.png" alt="Video groups with match bars" width="820"></p>

### Look closer

* Open the **film strip** to see frames of every copy next to each other.
* Press **Compare…** to open two files side by side with linked zoom and pan, a wipe slider, A/B flicker or a difference heat map; for videos with synchronised playback and quality scores.
* Use **Full screen** to walk through the groups one by one with the keyboard.

<p align="center"><img src="images/windows-timeline.png" alt="The film strip of a video group" width="820"></p>

More on all of this in [Results and clean-up](results-and-cleanup.md).

## 4 · Clean up safely

1. Press **Check duplicates** to tick, in every group, everything except the best file (or tick files yourself). **Delete nothing** unticks everything.
2. Choose **Quarantine** (recommended first) or **Recycle Bin**.
3. The program checks just before it moves anything that the files still exist and are unchanged, never removes a whole group, and never touches protected folders.
4. Afterwards you see how many files were moved and how much space you freed. The log (**Log…**) lets you undo.

<p align="center"><img src="images/windows-cleanup-done.png" alt="Three files moved to quarantine" width="640"></p>

Use your archive for a few days. When you are sure nothing is missing, empty the quarantine folder yourself.

> ⚠️ You decide what is removed and you are responsible for it. Look at a group before you delete. Keep a backup of everything you cannot afford to lose.

## What next?

* Change the sensitivity afterwards without scanning the folders again: on the results screen choose **Sensitivity…**, move the slider and press *Compare again*. See [Libraries and settings](settings.md#compare-again-with-another-sensitivity).
* Merge several backups into one clean archive: [Clean up backups](guides/clean-up-backups.md).
* Not sure why something was or was not found? See [How matching works](how-it-works.md) and the [FAQ](faq.md).
