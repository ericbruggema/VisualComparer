# Installation

[← Back to the overview](../README.md)

Visual Comparer comes in two forms. Both contain exactly the same program; pick what suits you.

| | Installer | Portable zip |
|---|---|---|
| File | `VisualComparer-<version>-Setup.exe` | `VisualComparer-<version>-portable-win-x64.zip` |
| Needs administrator rights | No (installs for your user), optional all-users install | No |
| Start menu entry, uninstaller | Yes | No |
| Writes to the registry | Only the standard uninstall entry | Nothing |
| Where your data lives | `data` folder inside the installation folder | `data` folder next to `VisualComparer.exe` |
| Update | Run the new installer over the old one | Unzip over a copy of the old folder, keep `data` |
| Remove | *Apps → Installed apps* (or the uninstaller) | Delete the folder |

## Requirements

* Windows 10 or Windows 11, 64-bit.
* About 175 MB of disk space (the program is self-contained and includes ffmpeg). No .NET installation is needed.
* An NVIDIA graphics card is optional; it speeds up video decoding. Any DirectX 12 card can be used for the optional GPU alignment mode.

## Install with the installer

1. Download `VisualComparer-<version>-Setup.exe` from the [latest release](https://github.com/ericbruggema/VisualComparer/releases/latest).
2. Start it. By default it installs **for your own user** in `%LOCALAPPDATA%\Programs\Visual Comparer`; no administrator rights are asked. If you want it for all users, choose that when the installer asks (it then installs in `C:\Program Files\Visual Comparer` and asks for administrator rights).
3. Read the licence, choose whether you want a desktop icon, and finish. The installer is available in English, Dutch and German.
4. Start **Visual Comparer** from the Start menu.

When the program is installed in a folder that normal users cannot write to (for example *Program Files*), it keeps its settings, libraries, results and cache in `%LOCALAPPDATA%\VisualComparer` instead.

### Silent install (for administrators)

```powershell
.\VisualComparer-1.0.0-Setup.exe /VERYSILENT /SUPPRESSMSGBOXES /NORESTART /CURRENTUSER
# all users, with administrator rights:
.\VisualComparer-1.0.0-Setup.exe /VERYSILENT /SUPPRESSMSGBOXES /NORESTART /ALLUSERS
```

## Use the portable version

1. Download `VisualComparer-<version>-portable-win-x64.zip` from the [latest release](https://github.com/ericbruggema/VisualComparer/releases/latest).
2. Unzip it to a folder you like, for example `C:\Tools\VisualComparer` or a USB stick. Avoid folders such as *Program Files* that need extra rights, because the program saves its settings and cache in a `data` folder next to `VisualComparer.exe`.
3. Start `VisualComparer.exe`.

The folder contains:

* `VisualComparer.exe`: the program (self-contained)
* `ffmpeg\`: ffmpeg 9.0.2 (GPL v3), which reads your videos and the photos Windows cannot read itself
* `lang\`: English, Dutch and German
* `LICENSE.txt`, `THIRD-PARTY-NOTICES.md`, `README.txt`

## Where is my data?

| Version | Location |
|---|---|
| Portable, or installed for your user | `data` next to `VisualComparer.exe` |
| Installed for all users (read-only program folder) | `%LOCALAPPDATA%\VisualComparer` |
| Custom | Set the environment variable `VC_DATA` to a folder of your choice |

The data folder holds your settings (`settings.json`), libraries and saved results, the fingerprint cache (a SQLite database), the action log and, after a crash, `crash.log`. **To move everything to another computer, copy that folder.** To start over, close the program and delete it. Files in your quarantine folder stay where they are until you delete them yourself.

## Check your download

Every release has a file `SHA256SUMS.txt` with a fingerprint of each download. If the fingerprint of your file is different, the file was damaged or changed: delete it and download again. In PowerShell:

```powershell
Get-FileHash .\VisualComparer-1.0.0-Setup.exe -Algorithm SHA256
```

Compare the result with the line in `SHA256SUMS.txt`.

## Windows warns about the file

The program is **not code-signed yet**. Windows SmartScreen may therefore say it "protected your PC" the first time you start the installer or the program, and some antivirus programs complain about new, unsigned programs. That is because the program is new and unsigned, not because it was found to be harmful.

* If you downloaded the file from this repository's releases page and the fingerprint matches, you can choose **More info**, then **Run anyway**.
* If you are not sure, **do not run it**. You can scan the file yourself first (for example with a free online checker).
* Files downloaded from other places than this repository's *Releases* page are not mine. Do not trust them.

## Update

* **Installer**: run the new installer. It replaces the program files and keeps your data.
* **Portable**: unzip the new version over a copy of the old folder and **keep your `data` folder**, so your libraries and cache stay.

New versions are announced on the [Releases](https://github.com/ericbruggema/VisualComparer/releases) page. The program never checks for updates by itself and never contacts any server.

## Remove

* **Installer**: *Settings → Apps → Installed apps → Visual Comparer → Uninstall*. At the end the uninstaller asks whether to remove your data folder too; answer *No* if you want to keep your libraries and cache (for example before installing a newer version).
* **Portable**: delete the folder.

## Language

The program follows the language of Windows (English, Dutch or German). You can choose another one under *Settings → Appearance → Language*; it takes effect after a restart. Adding a language takes one text file in the `lang` folder: copy `lang\en.json` to for example `lang\fr.json`, set `"_language"` to the name of the language in that language and translate the values on the right of the colons (leave the text on the left, and `{0}`, `{1}` ... in place).
