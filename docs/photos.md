# Photos

[← Back to the overview](../README.md)

How Visual Comparer treats photos: the five strictness levels, the two extra switches, the supported formats and how photos are read.

## Strictness: how much may two photos differ?

On the start screen (card 4, *How strict for photos*) you choose one of five levels. They go from "only exact file copies" to "also look-alikes".

| Level | Finds | Typical use |
|---|---|---|
| **Byte-identical** | Only files that are byte for byte the same. The fastest option; only files of equal size are read and compared. | A quick first pass; removing exact copies. |
| **Identical** | The exact same photo, even if it is smaller, saved in another format, re-saved, rotated or mirrored. **Not** one that is slightly different. | You want certainty: only the same photo, in any size or format. |
| **Same picture** *(default)* | Also light edits such as colour and brightness changes. | A good start for most archives. |
| **Similar** | Look-alikes. Follows the sensitivity setting. | A looser sweep after the first one. |
| **Loose** | Also burst shots and near-duplicates. Expect photos that are similar but **not** the same, so review these groups carefully. | Finding series of almost the same shot. |

> If two different-looking photos end up in one group, switch to a stricter level and scan again. You do not need to scan the folders again: on the results screen, **Sensitivity…** compares again from the cache.

### Two switches

* **Also rotated or mirrored** *(on by default)*: the photo is also recognised when it is turned by 90°, 180° or 270° or flipped left to right. Photos that carry an EXIF rotation (typical for phone photos) are shown as they look to you.
* **Also cropped** *(off by default)*: also finds a photo of which a piece was cut off, or that has a watermark or subtitles added. A bit less strict, so switch it on only when you expect cut-down versions.

## What the program tells you per photo

Each copy in a group shows the reason it matched next to its properties, for example:

* *smaller: 1200×900*
* *other format: BMP*
* *rotated 270°*
* *mirrored*
* *same picture* (a different file, identical picture)

The best copy is marked and kept by default. For photos, "best" means the **highest resolution first, then the largest file** (usually the least compressed). You can change the keep rules in Settings → *What to keep?*.

Press **Compare…** on a photo group to open the photo comparer: two copies side by side with **linked zoom and pan**, a **wipe slider**, **A/B flicker** and a **difference heat map**.

<p align="center"><img src="images/windows-photo-compare.png" alt="The photo comparer" width="800"></p>

## Supported formats

`.jpg` `.jpeg` `.jfif` `.png` `.webp` `.bmp` `.tif` `.tiff` `.gif` `.heic` `.heif` `.avif`

* HEIC, HEIF and AVIF work when Windows (with the installed codec extensions) or the bundled ffmpeg can decode them.
* Animated GIFs are compared by their first frame.
* **RAW camera files (CR2, NEF, ARW and similar) are not supported.** Export them to JPG or TIFF first if you want them compared.
* You can change the list of photo extensions in *Settings → Scan*.

## How photos are read

Photos are read with the **built-in Windows image reader** (WIC) inside the program. That is about ten times faster than the alternative of starting a separate ffmpeg program for every photo (measured on one thread: roughly 4 ms against 45 ms for a 1200×800 JPEG). JPEG files are even decoded at a reduced size straight away, so a 20-megapixel photo is never fully unpacked. If Windows cannot read a file, the bundled ffmpeg takes over automatically.

You can choose the behaviour in *Settings → Scan → How photos are read*:

| Option | Meaning |
|---|---|
| **Built-in reader first, ffmpeg if that fails** *(recommended)* | Fast, and still reads almost everything. |
| **Built-in reader only** | ffmpeg is never started for photos. Files Windows cannot read are reported as unreadable. |
| **ffmpeg only** | The slow way, but it reads the most formats. |

Photos that cannot be read at all (damaged, empty, not really an image) are listed in the **⚠ Broken videos** overview on the results screen (it lists unreadable photos too), so you can handle them yourself.

## Limits and good to know

* The minimum file size and duration filters apply to **videos only**; photos are small.
* Empty files are never reported as duplicates.
* Very large or extreme pictures (for example an image that is 8 pixels wide and 40,000 pixels high) are handled safely; the analysis picture is capped.
* Photos have **no EXIF display** (date, camera) in the results yet; you see format, dimensions, size and modification date.
* The first analysis of a large photo archive takes a while (every photo is read once). Later scans are fast. See [Performance](performance.md).
* The free edition handles up to **2,500 photos** per scan.
