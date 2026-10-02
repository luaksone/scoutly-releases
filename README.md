# Scoutly

[![Windows](https://img.shields.io/badge/Windows-1.12.25-0078D4?logo=windows11&logoColor=white)](https://github.com/luaksone/scoutly-releases/releases/latest)
[![Android](https://img.shields.io/badge/Android-1.4.25-3DDC84?logo=android&logoColor=white)](https://github.com/luaksone/scoutly-releases/releases/latest)
[![License](https://img.shields.io/badge/License-Freeware-4B5563)](LICENSE)
[![Latest release](https://img.shields.io/github/v/release/luaksone/scoutly-releases?label=Latest%20release&color=675CFF)](https://github.com/luaksone/scoutly-releases/releases/latest)

Scoutly is a local-first website monitor and price tracker for Windows and Android. It watches product pages and other web content, keeps a history of observed values, and alerts you when something changes.

This repository contains the official compiled releases. The application source code is not distributed here.

New to Scoutly? See the [getting-started guide](GETTING_STARTED.md) ([suomeksi](GETTING_STARTED_FI.md)) for creating a monitor and configuring ntfy notifications and encrypted Supabase synchronization.

## Latest package update

- Windows 1.12.25 and Android 1.4.25 reduce encrypted sync storage and database work. A representative listing-history fixture used 90.32% fewer encrypted bytes; actual savings depend on the data.
- The cloud keeps the newest 10,000 live runs or 16 MiB of run payloads, within the existing workspace quotas and retention. Full local history follows the device's existing retention settings. Monitors, settings, alerts, and deletion evidence are preserved.
- Essential data continues syncing when history cannot fit. Older backlog uploads cannot displace newer cloud history. Routine sync skips accepted history, empty local transactions, and unnecessary screen reloads.
- Fixes workspace-switch races, lost device-local request headers, Android history arriving before its monitor, and stale alert baselines after changing price type.
- Pairing reset requires a completed sync and is unavailable while paused, protecting newer cloud data.
- Updates the Electron runtime and affected build dependencies; dependency audits pass and packaging verifies installed versions against the lockfile.
- Android uses version code 40 and the existing upgrade-compatible signing certificate. The APK is non-debuggable; its certificate subject remains Android Debug.
- Retains the desktop sync-pause switch, S-kaupat browser transport, and startup recovery fixes. Upgrade while keeping existing app data.
- Independently signed update manifests are included. Windows executables remain unsigned by Authenticode.

**Supabase users:** Update both apps, export any history needed outside the devices, run [the complete Free Plan SQL upgrade](https://github.com/luaksone/scoutly-releases/releases/download/v1.12.25/Scoutly-Supabase-Free-Plan-1.12.25.sql) once in the existing project's SQL Editor, then restart both apps. Pairing codes remain valid. Installing the apps does not upgrade the hosted database. Older clients receive an update instruction once compressed data is published. Cloud history over the rolling budget is retired on maintenance; full local copies remain subject to local retention. [The SQL bundle and setup guide](https://github.com/luaksone/scoutly-releases/releases/download/v1.12.25/Scoutly-Supabase-1.12.25.zip) includes usage queries; encrypted payload counters exclude PostgreSQL row/index overhead and other project data.

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
| Windows | [Installer](https://github.com/luaksone/scoutly-releases/releases/download/v1.12.25/Scoutly-Setup-1.12.25-x64.exe) | 1.12.25 |
| Windows | [Portable application](https://github.com/luaksone/scoutly-releases/releases/download/v1.12.25/Scoutly-Portable-1.12.25-x64.exe) | 1.12.25 |
| Android | [APK](https://github.com/luaksone/scoutly-releases/releases/download/v1.12.25/Scoutly-Mobile-1.4.25-release.apk) | 1.4.25 |

The Windows installer adds Scoutly to the system normally. The portable build can be run without installation. Android may require permission to install applications from the browser or file manager used to open the APK.

## Data and privacy

Scoutly stores monitoring data locally. Network requests are made to the pages you choose to monitor and, when configured, to the location of your encrypted synchronization file. Scoutly does not require an account.

Website owners may restrict automated requests. You are responsible for configuring reasonable check intervals and using Scoutly in accordance with the terms and applicable rules of each website.

## Verifying downloads

SHA-256 hashes for the current packages are listed in [SHA256SUMS.txt](SHA256SUMS.txt).

On Windows, a downloaded file can be checked with PowerShell:

```powershell
Get-FileHash .\Scoutly-Setup-1.12.25-x64.exe -Algorithm SHA256
```

Compare the reported hash with the corresponding entry in `SHA256SUMS.txt`. Versions 1.12.18 / 1.4.19 also verify future releases against the publisher key embedded in the app and [signed release manifest](scoutly-release-manifest.json).

## License

Scoutly is distributed as freeware under the [Scoutly End User License Agreement](LICENSE). The agreement permits use of the compiled application and restricts reverse engineering, modification, and redistribution.
