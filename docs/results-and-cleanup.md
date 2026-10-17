# Results and clean-up

[← Back to the overview](../README.md)

How to read the result list, look closer, choose what to keep and remove files safely.

## Reading the result list

The results screen lists all groups below each other; the selected group is open. A group is one picture (or video) in several versions.

* **A row per file**: a switch (✓ keep / 🗑 remove), a thumbnail, its properties (dimensions, size, format, codec, duration) and why it matched.
* **The best file** is marked *best* and is the reference for the group. It is chosen by your [keep rules](#which-copy-is-the-best).
* **Photo groups** (📷) have no timeline; the photos are shown large next to each other. **Video groups** (🎬) have bars on a shared timeline.
* Above the list: **Previous group / Next group**, a search box, a sort menu (largest first, most files, name) and a filter *Videos and photos / Videos only / Photos only*.
* The summary line shows how many files are in how many groups, how many are marked for removal and how much space that frees.
* Press **Check duplicates** to mark, in every group, everything except the best file. **Delete nothing** unmarks everything. Marks stay when you remove other files.

<p align="center"><img src="images/windows-results-photos.png" alt="The result list for photos" width="820"></p>

### No duplicates?

You then see a clear message with the buttons *New scan* and *Search more sensitively*.

### Compare again with another sensitivity

Choose **Sensitivity…** on the results screen, move the slider (for example from 80% to 65%) and press *Compare again*. The program uses the list of files of the previous scan and the fingerprints from the cache: your folders are not searched and nothing is analysed again. Only a check that the files still exist, then candidates, comparing and grouping. The result shows the difference (groups and space, before and after). Your ticked choices are kept.

## Look closer

* **Film strip** (videos): frames of every copy next to each other. By default the first three videos of a group are shown; *Show more* loads the rest.
* **Compare…**: two files side by side with linked zoom and pan, wipe slider, A/B flicker, difference heat map and (for videos) synchronised playback with PSNR, SSIM and VMAF. See [Photos](photos.md) and [Videos](videos.md).
* **▶ Open** opens the selected file in its default program; **📁 In folder** shows it in Explorer.
* **Full screen review** walks through the groups one by one.

<p align="center"><img src="images/windows-review.png" alt="Full-screen review" width="820"></p>

Keyboard in the full-screen review: `←` `→` previous/next group · `Space` keep/remove · `Enter` next group. A strip at the top shows your progress (green = seen, outlined = current; click to jump).

## Which copy is the best?

*Settings → What to keep?* lets you order the rules that pick the best file of a group. They are applied from top to bottom; tick what counts:

1. Highest resolution
2. Longest duration
3. Highest bitrate
4. Preferred folder wins (you list the folders)
5. Newest file
6. Oldest file
7. Preferred codec (for example `hevc, av1, h264`)

Files in a **protected folder** always come first. For photos the highest resolution wins, then the largest file.

## Removing files safely

You can send the ticked files to the **Recycle Bin** (`Delete`) or to **quarantine** (`Ctrl+D`).

| | Quarantine | Recycle Bin |
|---|---|---|
| Restorable | Yes, with the log (**Undo**) | Through the Recycle Bin |
| Where | A folder you choose (default: inside the data folder). Choose a folder on the same drive for speed | The normal Windows Recycle Bin |
| Network drives | Works | Network drives have no Recycle Bin. The program asks once per session whether those files may be deleted permanently, otherwise it skips them |

**Start with quarantine.** Everything stays restorable until you empty the quarantine folder yourself.

### What protects you

* **A whole group is never removed at once**: at least one file is always kept.
* **Protected reference folders** (Settings → Safety): files in them are never removed and count as the original.
* **A quick check just before removing**: the file still exists and is unchanged. It costs nothing, even over the network. An optional extended check (Settings → Safety) re-reads both files and compares them again (slow).
* **A log with undo**: every move is written to the log (**Log…**); *Undo* puts the file back. If the original spot is taken it gets a new name (for example `photo (restored).jpg`).
* **Files in use**: if another program holds a file, the program tells you which one and offers to close it; otherwise the file stays where it is.
* **Cancel works immediately**, even in the middle of a large copy to quarantine; a half-copied file is cleaned up and the original is left alone.
* A progress window shows what is happening and afterwards the result: the number of files, the space freed and any problems.

<p align="center"><img src="images/windows-cleanup-done.png" alt="The result of a clean-up" width="620"></p>

### Common mistakes

* **Deleting from a synced folder.** If a folder is synced to the cloud, a delete may spread to other devices. Use a quarantine folder outside the synced folder.
* **Too loose a setting.** A loose photo level can group burst shots that are not the same. Review those groups carefully.
* **Not checking.** The match percentage is an indication. Look at the photos or the film strip before you remove anything.

## Export

From the results screen you can export the groups as **CSV**, **JSON** or an **HTML report with thumbnails** (one thumbnail per photo, a few per video, with dimensions, size and codec), to share or archive the outcome of a scan.

## Saved results

Results are saved **per library**: the groups, what you already ticked and where you were. This happens automatically after a scan, after every removal and shortly after each choice, and when you close the program. If you close the program (or it crashes) the results come back at the next start, and the program opens on the results if that is where you were. When loading, files are checked: whatever changed or disappeared drops out, and you see that in the message.

## Keyboard shortcuts

| Where | Key | Action |
|---|---|---|
| Results | `Delete` | Move ticked files to the Recycle Bin |
| Results | `Ctrl+D` | Move ticked files to quarantine |
| Full-screen review | `←` `→` | Previous / next group |
| Full-screen review | `Space` | Keep / remove the current file |
| Full-screen review | `Enter` | Next group |
| Video comparer | `Space` | Play / pause |
| Video comparer | `←` `→` | One frame back / forward (`Shift` = 1 s, `Ctrl` = 10 s) |
| Video comparer | `Home` | Back to the start |
| Comparers | `1`–`6` | Choose the view |
| Comparers | Mouse wheel / drag | Zoom / pan (linked on both sides) |
