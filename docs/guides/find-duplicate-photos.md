# How to find duplicate photos on Windows

[← Back to the overview](../../README.md) · [All guides](../../README.md#documentation)

Duplicate photos pile up quietly: phone backups, camera imports, downloads, edited copies. Here is how to find them, including copies that are smaller, rotated or saved in another format, and how to remove them safely.

## Why sorting by name or size is not enough

In Windows File Explorer you can sort by name, size or date. That finds files that are exactly the same, and only if you spot them yourself. It misses most real duplicates:

* a photo that was resized for email or messaging (different size, different file),
* the same picture saved as PNG instead of JPG,
* a copy that was rotated or flipped by another app,
* a copy that went through a backup or sync service and was renamed.

The picture is the same, but the file is not. To find those you have to compare what the photo *looks like*, not what the file is called.

## Step by step with Visual Comparer

1. **Install or unzip the program.** See [Installation](../installation.md).
2. **Add your folders.** Drag the folders with your photos onto the window, or use **＋ Folder…**. You can add several folders at once, including a backup drive.
3. Choose **Photos only** under *What to look for* if you only want photos. *Videos and photos* scans both in one go.
4. **Pick how strict to be.** *Same picture* is a good start: it finds the same photo even after resizing, a format change or a light edit. *Also rotated or mirrored* is on by default.
5. Press **Start scan**. The first scan analyses every photo once. Later scans only look at new or changed files, so they are fast.
6. **Read the groups.** Every group is one photo in several versions. The best one (by default the highest resolution) is marked and kept. Each copy says why it matched, for example "smaller", "other format" or "rotated 270°".
7. **Look before you delete.** Use **Compare…** to see two copies side by side with linked zoom, a wipe slider or a difference view.
8. **Clean up.** Press **Check duplicates** to tick all copies except the best one, then send them to **Quarantine** or the **Recycle Bin**.

<p align="center"><img src="../images/windows-results-photos.png" alt="A photo group in the results" width="780"></p>

## Which strictness should I use?

| Level | Meaning |
|---|---|
| **Byte-identical** | Only exact file copies. The fastest option. |
| **Identical** | The exact same photo, even if it is smaller, in another format or rotated. |
| **Same picture** | Also finds light edits such as colour and brightness changes. The default. |
| **Similar** | Look-alikes; follows the sensitivity setting. |
| **Loose** | Also burst shots and near-duplicates. Expect some photos that are similar but not the same, so review these groups carefully. |

More in [Photos](../photos.md).

## Tips for a safe clean-up

* Start with **Quarantine** instead of the Recycle Bin. Everything stays restorable until you empty the quarantine folder yourself.
* Mark your most trusted folder as a **protected reference folder**. Files in it are never removed.
* Keep a backup of photos you cannot replace. You decide what is deleted, and you are responsible for it.
* If two different-looking photos end up in one group, switch to a stricter level and scan again. You can change the sensitivity on the results screen without scanning the folders again.

## Which photo formats work?

JPG/JPEG/JFIF, PNG, WebP, BMP, TIFF and GIF, and HEIC/HEIF and AVIF when Windows or the bundled ffmpeg can decode them. RAW camera files are not supported.

Try it on a small folder first. The free edition handles up to 2,500 photos per scan.

## Related guides

* [Find resized, rotated or cropped copies of a photo](find-resized-rotated-cropped-photos.md)
* [Clean up duplicates after years of backups](clean-up-backups.md)
* [How to find duplicate videos on Windows](find-duplicate-videos.md)
