# Changelog

All notable changes to Visual Comparer for Windows. Downloads are on the [Releases](https://github.com/ericbruggema/VisualComparer/releases) page.

## 1.0.0 (free edition), first public release

**Finding duplicates**
* Photos and videos in one scan and one result list, in separate groups.
* Photos: five strictness levels (byte-identical, identical, same picture, similar, loose), optional matching of rotated, mirrored and cropped copies, EXIF rotation applied.
* Videos: three accuracy profiles (fast, normal, thorough); finds re-encodes, other resolution, bitrate or container, crops, black bars, rotation, mirroring, clips from a longer video, time shifts, speed changes, watermarks and burned-in subtitles.
* Scan modes: all vs all, folder A vs folder B, new vs library.
* Candidate index and fingerprint cache: scales to very large collections, repeat scans only analyse new or changed files.
* Photos are read with the built-in Windows image reader (about ten times faster than starting ffmpeg for each photo); ffmpeg is the fallback. Setting: *Settings → Scan → How photos are read*.
* Optional NVIDIA CUDA decoding and optional GPU alignment (DirectX 12).

**Results and comparing**
* The reason for every match, and for videos a bar on a shared timeline.
* Film strip, full-screen review with keyboard control.
* Comparer: side by side, wipe slider, A/B flicker, difference heat map, linked zoom and pan; for videos synchronised playback, frame stepping, PSNR, SSIM and VMAF.
* Change the sensitivity afterwards without scanning again.
* Libraries: several folder sets, results saved per library and restored after a restart.
* Export to CSV, JSON and HTML with thumbnails.

**Cleaning up safely**
* Recycle Bin or quarantine, undo log, protected reference folders, quick check before removing, never a whole group at once, cancel at any time.

**Progress and robustness**
* Progress with counters in every long step (finding files, analysing, grouping, preparing the result list, loading saved results, searching subfolders), also for archives of millions of files.
* Damaged settings, cache or database files are set aside and rebuilt instead of crashing; time limits on every ffmpeg call.

**Packaging**
* Installer (`-Setup.exe`, per user by default, optional all-users install, English/Dutch/German) and a portable zip.
* Languages: English, Dutch, German.

**Free edition**
* Up to 500 videos and 2,500 photos per scan.
