# How matching works

[← Back to the overview](../README.md)

This page explains, without code, how Visual Comparer decides that two files are "the same", what it can find and what it cannot. Understanding it helps you choose the right settings and judge the results.

## Why not just compare files?

A checksum or a file size changes the moment a single pixel changes. A photo that was resized for email, a video that was converted for the phone, or a picture that was saved again by a chat app is a **different file** even though you see **the same picture**. Comparing names, sizes or checksums only finds copies that were never touched. Visual Comparer compares what the files *look like*.

## The pipeline

A scan runs through five phases, which you can follow live on the scan screen.

1. **Finding files.** The folders are searched for photos and videos (by file extension), minus your exclusion patterns and filters. Network drives are skipped unless you allow them.
2. **Analysing.** Every file is read once and turned into a *fingerprint*. The fingerprint is stored in a local database (the cache), keyed by path, size and modification time, so unchanged files are never analysed again.
3. **Finding candidates.** Comparing every file with every other would take forever on a large archive. An *index* quickly selects only the pairs that could possibly match; the rest is excluded without comparing.
4. **Comparing.** The candidate pairs are compared in detail. For videos the two fingerprints are *aligned* in time, which is how clips, time shifts and speed changes are found.
5. **Grouping.** Pairs that match are merged into groups: if A matches B and B matches C, all three are one group. Inside a group the files are ranked with your keep rules; the best one is the reference.

## Fingerprints

### Photos

A photo is decoded and shrunk to a small greyscale picture. From it the program computes a short fingerprint of the light and dark areas of the picture (a perceptual hash). Photos that look the same get almost the same fingerprint, whatever their size, file format or name. The program also computes the fingerprints of the photo turned by 90°, 180° and 270° and mirrored, plus of slightly cropped versions, so it can recognise those variations.

For the stricter levels it also keeps a tiny 32×32 greyscale copy of the photo and compares it point by point (also turned and mirrored). That is what separates "the same photo" from "a photo that is only similar".

### Videos

From a video the program takes a picture every few seconds (the *accuracy profile* decides how often), removes black borders, and computes a fingerprint of each picture, again including rotated, mirrored and cropped variants and a variant of the top band of the picture (to ignore subtitles or a watermark). Flat or black frames are ignored because they say nothing.

The fingerprints of all pictures of a video together describe the video over time. Only the **picture** is compared, **not the sound**.

## Finding candidates quickly

Each fingerprint is cut into pieces; two similar fingerprints must share at least one piece (almost) exactly. An inverted index over those pieces finds, for each file, only the files that share a piece. This is *exact*: it gives the same result as comparing every pair, but takes minutes instead of hours on large archives. For videos, several pictures per video vote for a candidate; only pairs with enough votes are compared in detail.

Because of the index, the first scan of an archive is dominated by *reading* the files (once), while the comparing itself is fast.

## Aligning videos

Two videos that show the same film are not always lined up. One may start later, be a clip of the other, or play slightly faster (24 vs 25 frames per second). The comparer slides the fingerprint sequences along each other, with a small tolerance, to find the best overlap, and also tries a few speed ratios when equal speed does not fit. The result per pair is:

* the **match percentage**: how much of the shorter video is found in the other,
* the **offset** and, if needed, the **speed ratio**,
* which part matches (shown as the bar on the shared timeline),
* flags such as *cropped*, *rotated 90°*, *mirrored*, *watermark/subtitles*.

## What is found

| Change | Photos | Videos |
|---|:---:|:---:|
| Exact copy (same bytes) | ✓ | ✓ |
| Resized, recompressed, other format or container | ✓ | ✓ |
| Rotated 90°/180°/270° or mirrored | ✓ | ✓ |
| Light edits (colour, brightness) | ✓ (level *Same picture* or looser) | ✓ |
| Mildly cropped; black bars added | ✓ (switch on *Also cropped*) | ✓ |
| A clip taken from a longer video, other intro | – | ✓ |
| Other speed (e.g. 24 ↔ 25 fps) | – | ✓ (Normal or Thorough) |
| Watermark or burned-in subtitles | – | ✓ |
| Strongly cropped, heavily edited, collages | usually not | usually not |
| Same scene, different shot (burst photos, retakes) | only with *Loose* | no |

## What is not found, and why

* **Very short clips** (a few seconds) can be missed by the *Fast* profile, which takes few pictures. Use *Normal* or *Thorough*.
* **Heavily edited** pictures are different pictures for the program.
* **RAW camera files** are not read at all.
* **Sound** is ignored: two videos with the same picture and different audio are duplicates for the program.
* A fingerprint describes *how a picture looks*. Two **different** pictures that look alike (burst shots, screenshots of the same screen, a flat colour) can be grouped. That is why every group shows how strong the match is and why you should look before you delete.

## Sensitivity

The sensitivity slider (0–100%) sets how much two fingerprints may differ. A higher value finds more, looser matches (and more false ones), a lower value is stricter. For photos the strictness *level* matters more; for videos the sensitivity and the profile together. You can change the sensitivity **after** the scan: the program compares again from the cache without reading your folders.

## Cache and speed

* Fingerprints are cached per file; a later scan only analyses new or changed files.
* The cache is a local SQLite file in your data folder. Corrupt entries are ignored and re-read; a damaged database file is set aside as `.bad` and the cache starts over.
* Video decoding runs through ffmpeg, optionally on an NVIDIA graphics card (CUDA/NVDEC), which makes it several times faster for big videos. Photos are read with the built-in Windows image reader, about ten times faster than starting ffmpeg for every photo (see [Photos](photos.md#how-photos-are-read)).
* An optional mode aligns videos on the graphics card (DirectX 12). It gives exactly the same result as the processor.

## How strong is a match?

Each file in a group shows a percentage and a short reason. Use it as an *indication*, not as proof:

* **100%, "same picture"**: the picture is the same.
* **90–99%**: a very likely copy with small differences (another crop, a light edit).
* **lower**: look carefully; this is where look-alikes and partial copies live.

When in doubt, open **Compare…** and look with your own eyes.
