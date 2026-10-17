# FAQ and troubleshooting

[← Back to the overview](../README.md)

Short answers to the questions people ask most. Nothing here replaces looking at your files yourself before you delete them.

* [Using the program](#using-the-program)
* [The free edition](#the-free-edition)
* [What does it not do well?](#what-does-it-not-do-well)
* [Privacy](#privacy)
* [Problems](#problems)

## Using the program

**Where do I start?**
Start `VisualComparer.exe`, drop a folder on the window and press **Start scan**. [Getting started](getting-started.md) shows every step. Inside the program the **? Guide** button opens a short interactive introduction.

**What is the best way to clean up a pile of backups?**
Put the backup folders in one scan (*All vs all*), mark your most trusted folder as a protected reference folder, scan, review each group and send the ticked files to quarantine first. Delete the quarantine folder only when you are sure. Next time, use *New vs library* to check only new files. See [Clean up backups](guides/clean-up-backups.md).

**Which formats does it read?**
Photos: JPG, JPEG, JFIF, PNG, WebP, BMP, TIFF, GIF, HEIC, HEIF and AVIF (the last three when Windows or the bundled ffmpeg can decode them). Videos: MP4, MKV, AVI, MOV, WMV, FLV, WebM, M4V, MPG, MPEG, TS, M2TS, MTS, 3GP, OGV, VOB and DIVX. RAW camera files are not supported.

**Why was a copy not found?**
Matching is based on the picture. Heavily edited, strongly cropped or very short copies can be missed, and the *Fast* video profile skips speed changes and short clips. Try a looser setting, use the *Thorough* profile, or change the sensitivity on the results screen: it compares again from the cache without scanning the folders. See [How matching works](how-it-works.md#what-is-not-found-and-why).

**Why were two different files grouped?**
Look-alikes happen, especially with burst shots, screenshots of the same screen or loose settings. The match strength is shown for each file. Look before you delete and use a stricter setting (for photos: *Identical* or *Same picture*).

**The first scan takes long. Is that normal?**
Yes. Every photo and video is analysed once. Later scans only analyse new or changed files. An NVIDIA card (CUDA) speeds up video, and network drives are slower than local drives. See [Performance](performance.md).

**Where are my settings and cache?**
In the `data` folder next to `VisualComparer.exe`. If that folder cannot be written to (for example in *Program Files*), the program uses `%LOCALAPPDATA%\VisualComparer` instead. Copy the folder to move your libraries to another computer. See [Installation](installation.md#where-is-my-data).

**Can I change the language?**
Yes: *Settings → Appearance → Language* (English, Dutch, German). It takes effect after a restart. Adding a language takes one text file in the `lang` folder.

**The Recycle Bin does not work on my network drive.**
Network drives have no Recycle Bin. The program asks once per session whether those files may be deleted permanently; otherwise it skips them. Quarantine is the safer choice.

**Can I undo a clean-up?**
Yes, if you used quarantine: open the log (**Log…**) and use *Undo*. Files moved to the Recycle Bin can be restored from there.

**Can I scan a folder on a network drive or an external disk?**
Yes; tick *Include network drives* in *Settings → Scan*. It is slower than a local disk.

**Does it compare sound?**
No, only the picture.

## The free edition

**What are the limits?**
A scan processes up to **500 videos** and **2,500 photos**; photos and videos have their own limit. Everything else works without restrictions.

**What happens when I have more files than that?**
The scan runs on the first files in the order of your folders and the program tells you how many files were skipped. Everything below the limit works as usual. You can scan the remaining folders in another run, or scan fewer folders at once.

**Does it need the internet?**
No. The program never contacts any server.

## What does it not do well?

* **Heavily edited or strongly cropped copies** can be missed: they are different pictures for the program.
* **Very short video clips** (a few seconds) can be missed by the *Fast* profile; use *Normal* or *Thorough*.
* **Look-alikes** (burst shots, screenshots of the same screen) can be grouped, especially at the *Similar* and *Loose* photo levels.
* **Sound is ignored.**
* **RAW camera files** are not read.
* **Very large archives** need time for the first analysis and several GB of memory when comparing millions of photos.
* A **match percentage is an indication**, not proof. Always look before you delete.

## Privacy

**What does the program send?**
Nothing. Your photos, videos, folder names and scan results stay on your computer. There is no account and no telemetry, and the program does not contact any server. The only network use is by you: opening the project page in your browser from the *About* tab.

**Does ffmpeg send anything?**
No. It is started as a separate local program that reads your files; it does not use the network here.

## Problems

**Windows or my antivirus warns about the file.**
The program is not code-signed yet, which triggers warnings for new programs. See [Installation](installation.md#windows-warns-about-the-file) for how to check the fingerprint and what to do. If you are not sure, do not run it.

**The program crashed.**
A `crash.log` is written next to the program (or in the data folder). Close the program, start it again and scan again: what was already analysed is kept in the cache. If it keeps happening, open an [issue](https://github.com/ericbruggema/VisualComparer/issues) and attach `crash.log` (check it for private folder names first).

**A scan is slow or seems stuck.**
Check the phase and the counters on the scan screen. During *Analysing* the program reads every file; a network drive or a damaged file can be slow. A file that does not answer within 60 seconds is skipped and listed as broken. You can cancel at any time and continue later: nothing analysed is lost.

**Some files are listed as broken.**
They could not be read (damaged, empty, not really a photo or video, or a format that is not supported). Open **⚠ Broken videos** to see them; you can send them to quarantine or the Recycle Bin from there.

**HEIC or AVIF photos are not read.**
They are read when Windows has the codec (for example the *HEIF Image Extensions* from the Microsoft Store) or when the bundled ffmpeg can decode them. Otherwise convert them to JPG first.

**The settings window or results look strange after an update.**
Close the program and delete `settings.json` in the data folder. (Your libraries and cache are separate files and stay.)

**Where can I report a bug or ask something?**
Use the [issue tracker](https://github.com/ericbruggema/VisualComparer/issues) or the contact options on ericbruggema.nl. There is no guaranteed support or response time.

---

Always keep a backup of files you cannot lose. You are responsible for what you delete.
