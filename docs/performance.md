# Performance

[← Back to the overview](../README.md)

What to expect from a scan, what makes it slow or fast, and how the program stays responsive on big collections.

> **Free edition limit:** a scan processes up to **500 videos** and **2,500 photos**. The numbers on this page describe how the engine behaves in tests with much larger collections; with the free edition a scan is limited to the first files in the order of your folders. If a scan was cut short you see how many files were skipped.

## Where the time goes

| Phase | What dominates it | What helps |
|---|---|---|
| Finding files | The speed of the drive; a network drive is much slower than a local one | Local drives; exclude folders you do not need |
| **Analysing** | **Reading every photo and video once** | The cache: the next scan only analyses new or changed files. A fast SSD. For video: an NVIDIA card (CUDA) |
| Finding candidates | Almost nothing; an index selects the pairs | – |
| Comparing | For videos: aligning the remaining pairs. For photos: very little | Compare resolution (Settings → Compare), optional GPU alignment |
| Grouping | Very little | – |

The **first scan** of a collection is therefore always the slowest; after that, almost everything comes from the cache and a scan takes seconds to minutes.

## Photos

* Photos are decoded with the built-in Windows image reader. In a test on one thread, a 1200×800 JPEG took about 4 ms with the built-in reader against about 45 ms when ffmpeg is started for every photo, roughly **ten times faster**. Many photos are read in parallel.
* The comparison switches from "compare every pair" to an **index** at 4,000 photos. The result is exactly the same, but much faster: in a synthetic test with two million photos the comparing phase took about five minutes, where comparing all pairs would need about 2×10¹² comparisons.
* Memory: about 1.2 KB per photo while comparing (the fingerprint and a 32×32 picture), so roughly 3–5 GB for two million photos.

## Videos

* Each video is read once; a picture is taken every few seconds (the accuracy profile decides how often).
* **CUDA / NVDEC** decodes and shrinks on the graphics card (automatic from 720p upwards). In tests on an RTX-class laptop a 2-minute 4K HEVC video went from about 31 s on the processor to about 6 s.
* Fingerprints made with the processor and with CUDA differ by about one bit on average; they can be mixed.
* An index finds the candidate pairs (60 of 60 planted duplicates were found among 5,000 fingerprints in 1.3 s, with 0.002% false candidates).
* Aligning on the graphics card (optional) gives the same result as the processor and helps with many long videos.

## Staying responsive

* Progress messages are throttled to a few per second, so a huge scan does not flood the window; the counters keep moving.
* Searching a very large folder tree for subfolders runs in a separate progress window with a counter and a cancel button.
* Long steps after the scan (grouping, preparing the result list, loading saved results) show their own progress.
* **Cancel** works at any time. What was already analysed is kept in the cache.

## Tips

* Scan on a **local drive** when you can; copy from a network drive first if you scan the same data often.
* Use **Fast** for a first rough check of videos and **Normal** for daily use.
* Leave **Automatic** for the number of videos analysed at the same time unless your GPU or processor is clearly not fully used; then try 10–16.
* Close programs that use the disk heavily during the first scan.
* Do the first scan of a big collection when you do not need the PC. A later scan is quick.
