# Clean up duplicates after years of backups

[← Back to the overview](../../README.md) · [All guides](../../README.md#documentation)

Phone backup, cloud sync, an old laptop, a USB drive, then a new hard drive. If you back up all the time, you end up with the same photos and videos in many places. This guide shows how to merge them into one clean archive without losing anything you care about.

## Before you start

* **Make one more backup** of the most important files before cleaning up. A clean-up changes your files, and you stay responsible for the result.
* **Decide which folder you trust most.** That will be your reference.
* **Connect all drives** that hold backups. Local drives are much faster than network drives.

## Plan A: merge everything in one scan

1. Add all backup folders to Visual Comparer, for example the phone backup, the old laptop folder and the archive drive.
2. Choose **All vs all**, and *Videos and photos* if you have both.
3. In the settings, add your trusted folder as a **protected reference folder**, and as a **preferred folder** so it wins when two copies are equal. Files in a protected folder are never removed.
4. Scan. Copies of the same photo or video, wherever they are stored, end up in one group.
5. Review the groups, press **Check duplicates**, and send the ticked files to **Quarantine**.
6. Use your archive for a few days. When you are sure nothing is missing, empty the quarantine folder.

## Plan B: compare one backup against another

Use **Folder A vs folder B** when you only want to know what is in the old backup that is also in the new one. Put the old backup in A and the new one in B. It only reports copies between the two sets, not copies inside one set.

## Plan C: check new photos against what you already have

After the first big clean-up, use **New vs library**. Every time you import or back up new files, the program compares them with everything it has scanned before. Because earlier files are in the cache, this is fast.

## Keep your results

A **library** keeps your folder sets, settings and results together, for example "Family photos" and "Work videos". Results are saved per library, so you can continue after a restart. If you change the sensitivity later, the program compares again from the cache without scanning the folders. See [Libraries and settings](../settings.md).

## Common mistakes

* **Deleting from a synced folder.** If a folder is synced to the cloud, a delete may spread to other devices. Quarantine outside the synced folder.
* **Network drives have no Recycle Bin.** Use quarantine, or the program will ask before deleting permanently.
* **Too loose a setting.** A loose photo setting can group burst shots that are not the same. Review those groups carefully.
* **Not checking.** A match percentage is an indication. Look at the photos or the film strip before you remove anything.

Start with one backup folder. The free edition processes up to 500 videos and 2,500 photos per scan.

## Related guides

* [How to find duplicate photos on Windows](find-duplicate-photos.md)
* [How to find duplicate videos on Windows](find-duplicate-videos.md)
