# Scoutly

[![Windows](https://img.shields.io/badge/Windows-1.12.15-0078D4?logo=windows11&logoColor=white)](https://github.com/luaksone/scoutly-releases/releases/latest)
[![Android](https://img.shields.io/badge/Android-1.4.16-3DDC84?logo=android&logoColor=white)](https://github.com/luaksone/scoutly-releases/releases/latest)
[![License](https://img.shields.io/badge/License-Freeware-4B5563)](LICENSE)
[![Latest release](https://img.shields.io/github/v/release/luaksone/scoutly-releases?label=Latest%20release&color=675CFF)](https://github.com/luaksone/scoutly-releases/releases/latest)

Scoutly is a local-first website monitor and price tracker for Windows and Android. It watches product pages and other web content, keeps a history of observed values, and alerts you when something changes.

This repository contains the official compiled releases. The application source code is not distributed here.

New to Scoutly? See the [getting-started guide](GETTING_STARTED.md) ([suomeksi](GETTING_STARTED_FI.md)) for creating a monitor and configuring ntfy notifications and encrypted Supabase synchronization.

## Latest package update

- Monitor checks now lengthen their effective interval automatically after repeated HTTP 403, 408, 425, 429, or 503 responses, with a configurable trigger threshold and automatic recovery after a successful check.
- Offer magazines now support comfortable and compact layouts, hiding and restoring retailers, and synchronized pinned/hidden preferences across Windows and Android.
- Price Finder remains marked experimental and is separated into the desktop Tools section.
- Request-refusal messages and structured error logging are consistent across both applications.

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
| Windows | [Installer](Scoutly-Setup-1.12.15-x64.exe) | 1.12.15 |
| Windows | [Portable application](Scoutly-Portable-1.12.15-x64.exe) | 1.12.15 |
| Android | [APK](Scoutly-Mobile-1.4.16-debug.apk) | 1.4.16 |

The Windows installer adds Scoutly to the system normally. The portable build can be run without installation. Android may require permission to install applications from the browser or file manager used to open the APK.

## Data and privacy

Scoutly stores monitoring data locally. Network requests are made to the pages you choose to monitor and, when configured, to the location of your encrypted synchronization file. Scoutly does not require an account.

Website owners may restrict automated requests. You are responsible for configuring reasonable check intervals and using Scoutly in accordance with the terms and applicable rules of each website.

## Verifying downloads

SHA-256 hashes for the current packages are listed in [SHA256SUMS.txt](SHA256SUMS.txt).

On Windows, a downloaded file can be checked with PowerShell:

```powershell
Get-FileHash .\Scoutly-Setup-1.12.15-x64.exe -Algorithm SHA256
```

Compare the reported hash with the corresponding entry in `SHA256SUMS.txt`.

## License

Scoutly is distributed as freeware under the [Scoutly End User License Agreement](LICENSE). The agreement permits use of the compiled application and restricts reverse engineering, modification, and redistribution.
