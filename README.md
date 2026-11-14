# Scoutly

[![Windows](https://img.shields.io/badge/Windows-1.12.34-0078D4?logo=windows11&logoColor=white)](https://github.com/luaksone/scoutly-releases/releases/latest)
[![Android](https://img.shields.io/badge/Android-1.4.34-3DDC84?logo=android&logoColor=white)](https://github.com/luaksone/scoutly-releases/releases/latest)
[![License](https://img.shields.io/badge/License-Freeware-4B5563)](LICENSE)
[![Latest release](https://img.shields.io/github/v/release/luaksone/scoutly-releases?label=Latest%20release&color=675CFF)](https://github.com/luaksone/scoutly-releases/releases/latest)

Scoutly is a local-first website monitor and price tracker for Windows and Android. It watches product pages and other web content, keeps a history of observed values, and alerts you when something changes.

This repository contains the official compiled releases. The application source code is not distributed here.

New to Scoutly? See the [getting-started guide](GETTING_STARTED.md) ([suomeksi](GETTING_STARTED_FI.md)) for creating a monitor and configuring ntfy notifications and encrypted Supabase synchronization.

## Latest package update

Windows 1.12.34 and Android 1.4.34 tell you when sync stops working, make list monitors behave the same on both devices, free disk space that old downloads took on Windows, and update both apps' components. See the [full release notes](https://github.com/luaksone/scoutly-releases/releases/tag/v1.12.34). Both apps offer this release as an in-app update from 1.12.33 / 1.4.33.

- **Sync alerts:** Scoutly for Windows notifies you, also on your phone through ntfy, when sync has failed for a day or been paused for three. The Android app notifies you when its own sync fails or when the monitors that Scoutly for Windows checks stop receiving results. Settings → Sync on Windows can copy a diagnostics report and open the new log file.
- **List monitors:** after a check on the phone, Scoutly for Windows no longer sends a second "changed" alert for an unchanged list. Both apps now see a list as changed when any item changes, and the new-items chart on Windows counts the items the phone found first.
- **Windows:** installers of already installed updates are deleted, and recovery copies and the old storage file go to the Recycle Bin after 30 days, which can free more than a gigabyte. Deleting the sync workspace or resetting the pairing code works for large workspaces too. Electron 45 brings Chromium 156 security fixes.
- **Android:** updated components. The APK uses version code 49 and the existing upgrade-compatible signing certificate.

**Supabase users:** run [the complete Free Plan SQL upgrade](https://github.com/luaksone/scoutly-releases/releases/download/v1.12.34/Scoutly-Supabase-Free-Plan-1.12.34.sql) once in the existing project's SQL Editor. It adds step-by-step clearing for workspace deletion and pairing resets; everything else is as in 1.12.33. Restarting the apps and pairing again are not needed, and installing the apps does not upgrade the hosted database. Apps from 1.12.25 / 1.4.25 keep working with it. [The SQL bundle and setup guide](https://github.com/luaksone/scoutly-releases/releases/download/v1.12.34/Scoutly-Supabase-1.12.34.zip) includes usage queries.

## What Scoutly does

Scoutly can be used to:

- monitor product prices and stock availability;
- track numeric values or selected content on a web page;
- retain a history of observations and display hourly, daily, or monthly changes over time;
- compare related listings from different websites;
- notify you when a monitored value changes;
- use the same encrypted workspace on Windows and Android.

Price monitoring distinguishes a product's main price from unit prices such as price per item, kilogram, or litre. Scoutly also filters page elements such as cart totals and unrelated promotional values that should not become the monitored price.

## Desktop and mobile applications

Both applications can create and manage price monitors, run checks independently, and review synchronized history. Android can discover a product price directly from its page URL without requiring a desktop browser or a CSS selector.

The Windows application also provides listing comparison, correction, and advanced site-training tools. Android provides manual and background checks, system notifications, and hourly, daily, and monthly charts. An encrypted synchronization file can share monitor and alert data between devices without requiring a Scoutly account or hosted Scoutly service.

## Downloads

| Platform | Package | Version |
| --- | --- | --- |
| Windows | [Installer](https://github.com/luaksone/scoutly-releases/releases/download/v1.12.34/Scoutly-Setup-1.12.34-x64.exe) | 1.12.34 |
| Windows | [Portable application](https://github.com/luaksone/scoutly-releases/releases/download/v1.12.34/Scoutly-Portable-1.12.34-x64.exe) | 1.12.34 |
| Android | [APK](https://github.com/luaksone/scoutly-releases/releases/download/v1.12.34/Scoutly-Mobile-1.4.34-release.apk) | 1.4.34 |

The Windows installer adds Scoutly to the system normally. The portable build can be run without installation. Android may require permission to install applications from the browser or file manager used to open the APK.

## Data and privacy

Scoutly stores monitoring data locally. Network requests are made to the pages you choose to monitor and, when configured, to the location of your encrypted synchronization file. Scoutly does not require an account.

Website owners may restrict automated requests. You are responsible for configuring reasonable check intervals and using Scoutly in accordance with the terms and applicable rules of each website.

## Verifying downloads

SHA-256 hashes for the current packages are listed in [SHA256SUMS.txt](SHA256SUMS.txt).

On Windows, a downloaded file can be checked with PowerShell:

```powershell
Get-FileHash .\Scoutly-Setup-1.12.34-x64.exe -Algorithm SHA256
```

Compare the reported hash with the corresponding entry in `SHA256SUMS.txt`. Versions 1.12.18 / 1.4.19 also verify future releases against the publisher key embedded in the app and [signed release manifest](scoutly-release-manifest.json).

## License

Scoutly is distributed as freeware under the [Scoutly End User License Agreement](LICENSE). The agreement permits use of the compiled application and restricts reverse engineering, modification, and redistribution.
