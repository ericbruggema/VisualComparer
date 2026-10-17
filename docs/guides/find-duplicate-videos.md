# How to find duplicate videos on Windows

[← Back to the overview](../../README.md) · [All guides](../../README.md#documentation)

Videos take the most space, and the same video is often stored more than once: re-encoded, shrunk for the phone, cut shorter, or copied between drives. Here is how to find those copies and keep the best one.

## Why the same video looks like a different file

A video is not like a text file. The moment it is converted, shrunk, trimmed or exported again, the file changes completely, even though you see the same film. Comparing file names, sizes or checksums only finds copies that were never touched. Real-life duplicates usually look like this:

* a smaller copy for the phone or a tablet (other resolution or bitrate),
* the same video in another container, for example MKV instead of MP4,
* a clip that was cut from a longer video,
* a copy with black bars, a watermark or burned-in subtitles,
* a copy at another speed, such as 24 versus 25 frames per second.

## Step by step with Visual Comparer

1. **Start the program** and drag your video folders onto the window. See [Installation](../installation.md) if you have not installed it yet.
2. Choose **Videos only** under *What to look for*, or keep *Videos and photos*.
3. **Pick the video accuracy.** *Normal* takes a picture every 1 to 4 seconds depending on the length and is a good balance. *Fast* is for a first rough check. *Thorough* is for short clips and speed changes.
4. **Start the scan.** If you have an NVIDIA card, leave CUDA on to speed up decoding. Every video is analysed once; after that the results come from the cache.
5. **Read the timeline.** Each group shows one video in several versions. The bar on a shared timeline shows which part of each copy matches the best version: a full bar for a full copy, a short bar for a clip.
6. **Check with your own eyes.** Click on a bar and every copy jumps to the same scene. Open the film strip to compare frames, or use **Compare…** for side by side, a wipe slider, a difference view and PSNR, SSIM and VMAF scores.
7. **Clean up.** Tick the copies you do not need and move them to **Quarantine** or the **Recycle Bin**. The best version, by your rules (for example the highest resolution or the preferred folder), is kept.

<p align="center"><img src="../images/windows-results-videos.png" alt="Video groups with bars on a shared timeline" width="780"></p>

## Good to know

* Only the picture is compared, not the sound.
* The *Fast* profile can miss speed changes and very short clips. Use *Normal* or *Thorough* for those.
* A clip shows up in the group of the longer video, with a shorter bar, so you see that it is only part of it.
* Damaged files that cannot be read are listed separately, so you can handle them yourself.
* The first scan of a big library takes a while. Later scans only analyse new or changed files.
* The free edition handles up to 500 videos per scan.

## Which video formats work?

MP4, MKV, AVI, MOV, WMV, FLV, WebM, M4V, MPG, MPEG, TS, M2TS, MTS, 3GP, OGV, VOB and DIVX. You can change the list of extensions in the settings.

More in [Videos](../videos.md).

## Related guides

* [How to find duplicate photos on Windows](find-duplicate-photos.md)
* [Clean up duplicates after years of backups](clean-up-backups.md)
