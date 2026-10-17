# Third-party components (Windows)

Visual Comparer itself is proprietary freeware; see `LICENSE.txt`. It uses the components below, each under its own licence.
The licences of these components apply to them only; nothing in `LICENSE.txt` restricts the rights they give you.

| Component | Used for | Licence |
|-----------|----------|---------|
| **FFmpeg** 9.0.2 "release essentials" build from <https://www.gyan.dev/ffmpeg/builds/> (`ffmpeg\ffmpeg.exe`) | Decoding photos and videos, thumbnails, PSNR/SSIM/VMAF. Started as a separate program; Visual Comparer is not linked with it. | GPL v3 (the build contains GPL components). Licence text: `ffmpeg\LICENSE`. |
| **libvmaf** (inside the FFmpeg build) | VMAF score | BSD-2-Clause + Patent |
| **Microsoft.Data.Sqlite**, SQLitePCLRaw, SQLite | Fingerprint cache and action log | MIT / Apache-2.0 / public domain |
| **ComputeSharp** by Sergio Pedri | Optional alignment on the graphics card (DirectX 12 compute) | MIT |
| **.NET 10** runtime and WPF | Program environment (self-contained) | MIT |

## FFmpeg source code (GPL v3)

The `ffmpeg.exe` that is shipped with Visual Comparer is an **unmodified** build made by gyan.dev. The corresponding source code is available:

* FFmpeg source for the exact commit this build was made from: <https://github.com/FFmpeg/FFmpeg/commit/946fcce07b>
* Build scripts and build configuration: <https://www.gyan.dev/ffmpeg/builds/> (the full configuration is printed in `ffmpeg\README.txt`)
* General FFmpeg downloads: <https://ffmpeg.org/download.html>

If you cannot get the source from these places, ask for a copy through the contact details in the repository README. It will be provided for no more than the cost of
physically performing the distribution, as required by the GPL v3 (section 6).
