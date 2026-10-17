# Find resized, rotated or cropped copies of a photo

[← Back to the overview](../../README.md) · [All guides](../../README.md#documentation)

The same photo can exist as a small copy from a chat app, a rotated copy from a scanner, a PNG from a screenshot tool, or a mirrored copy from an editor. A normal search never connects them. This guide explains how matching by picture works and how to use it.

## What "the same photo" means to a computer

A checksum changes when a single pixel changes, so a resized photo gets a totally different one. Visual Comparer works differently: it makes a small, grey, simplified version of the picture and turns it into a short fingerprint of its light and dark areas. Photos that look the same get almost the same fingerprint, whatever their size, format or file name. It also checks the fingerprint of the photo turned by 90, 180 and 270 degrees and mirrored. See [How matching works](../how-it-works.md).

## What it finds

| Change | Found? | How |
|---|:---:|---|
| Resized or compressed more | ✓ | Strictness *Identical* or higher |
| Saved in another format (JPG, PNG, WebP, BMP, TIFF…) | ✓ | Any picture-based level |
| Rotated 90°, 180°, 270° or mirrored | ✓ | *Also rotated or mirrored* (on by default) |
| Light edits: colour, brightness | ✓ | *Same picture* or looser |
| Mildly cropped | ✓ | Switch on *Also cropped* |
| Strongly cropped, heavily edited, collages | often not | These are different pictures for the program |

## How to do it

1. Start the program, add your folders and choose **Photos only**.
2. Choose strictness **Same picture**. Keep **Also rotated or mirrored** on, and switch on **Also cropped** if you expect cut-down versions.
3. Scan, and open a group. The line next to each copy explains the match, for example "smaller: 1200×900 · other format: BMP" or "rotated 270°".
4. Press **Compare…** to put two copies side by side. Zoom and pan are linked, and a wipe slider or difference view shows exactly what changed.
5. Keep the version you want, normally the one with the highest resolution, and send the rest to **Quarantine**.

<p align="center"><img src="../images/windows-photo-compare.png" alt="Two copies of a photo side by side" width="780"></p>

## Tips

* The "best" copy is chosen by your keep rules: highest resolution first, then the largest file (usually the least compressed). You can change the rules in the settings.
* If you want to keep a rotated copy because it is the one that is correct, untick the one you want and tick the other. The program does not decide for you.
* RAW camera files are not supported. Export them to JPG or TIFF first if you want them compared.
* Always keep a backup of photos you cannot replace.

## Related guides

* [How to find duplicate photos on Windows](find-duplicate-photos.md)
* [Clean up duplicates after years of backups](clean-up-backups.md)
