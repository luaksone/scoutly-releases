# Scoutly

[![Windows](https://img.shields.io/badge/Windows-1.12.26-0078D4?logo=windows11&logoColor=white)](https://github.com/luaksone/scoutly-releases/releases/latest)
[![Android](https://img.shields.io/badge/Android-1.4.26-3DDC84?logo=android&logoColor=white)](https://github.com/luaksone/scoutly-releases/releases/latest)
[![License](https://img.shields.io/badge/License-Freeware-4B5563)](LICENSE)
[![Latest release](https://img.shields.io/github/v/release/luaksone/scoutly-releases?label=Latest%20release&color=675CFF)](https://github.com/luaksone/scoutly-releases/releases/latest)

Scoutly is a local-first website monitor and price tracker for Windows and Android. It watches product pages and other web content, keeps a history of observed values, and alerts you when something changes.

This repository contains the official compiled releases. The application source code is not distributed here.

New to Scoutly? See the [getting-started guide](GETTING_STARTED.md) ([suomeksi](GETTING_STARTED_FI.md)) for creating a monitor and configuring ntfy notifications and encrypted Supabase synchronization.

## Latest package update

Windows 1.12.26 and Android 1.4.26 make adding a monitor on the phone quick and include the fixes from a full code review of both apps. The [release notes](https://github.com/luaksone/scoutly-releases/releases/tag/v1.12.26) list every change.

**Install this version manually.** The update-signing key has changed, so 1.12.25 and earlier will not offer this release as an in-app update. Install Setup and the APK below over your current version; monitors, history and settings are kept. In-app updates work again from 1.12.26 / 1.4.26 on.

**Android 1.4.26**

- **Share to Scoutly:** in the browser, choose Share and then **Monitor with Scoutly**. The editor opens with the address filled in and the price already detected. Saving returns to the browser and runs the first check.
- **New monitor shortcut:** long-press the app icon. The Overview page also has a New monitor button.
- **Simpler editor:**
  - a paste button;
  - a warning for pages you already monitor;
  - one-tap choices for what to track, when to alert and how often to check;
  - an always-visible Save.
- **Not the right price?** lets you pick another verified price from the page.
- **Background checks run again on Android 12 and later while the app is closed.** A failing sync no longer slows scheduled checks to once every five hours.
- **Fixes:** decimal-comma target prices, duplicate monitors from a double tap, merged old/new prices, empty values read as "null", new-item alert floods, and unsupported desktop alert rules. A phone coming back online shows at most five alert notifications.
- Android uses version code 41 and the existing upgrade-compatible signing certificate. The APK is non-debuggable; its certificate subject remains Android Debug.

**Windows 1.12.26**

- **Prices:** "$1,299" and "1.299 €" read as thousands, and monitors that stored the old reading recover automatically. A selector that stops matching no longer switches to a related product's price.
- **Reliability:** automatic price detection no longer freezes on number-heavy pages, and browser checks no longer grow memory. Queued monitors can be edited, and failed checks back off.
- **Alerts:** Finnish, Swedish and German out-of-stock labels are recognised, and slow deliveries no longer send an alert twice.
- **Sync:** restoring the startup backup no longer overwrites newer data on other devices, and **Create encrypted workspace** works again. The sync index stays bounded, and settings no longer bounce between devices.
- **Screens:** save errors appear in the editor, background sync keeps unsaved Settings edits, and the Finnish interface no longer translates monitor names or page values.
- Security updates: Electron 43.8.7, re2js 2.9.1 and Android jsoup 1.23.2 address newly published advisories; dependency audits pass.
- Independently signed update manifests are included. Windows executables remain unsigned by Authenticode. Upgrade while keeping existing app data.

**Supabase users:** no SQL change in this release. Projects already upgraded with the 1.12.25 SQL need no action. Otherwise run [the complete Free Plan SQL upgrade](https://github.com/luaksone/scoutly-releases/releases/download/v1.12.26/Scoutly-Supabase-Free-Plan-1.12.26.sql) once in the existing project's SQL Editor, then restart both apps. Pairing codes remain valid, and installing the apps does not upgrade the hosted database. [The SQL bundle and setup guide](https://github.com/luaksone/scoutly-releases/releases/download/v1.12.26/Scoutly-Supabase-1.12.26.zip) includes usage queries.

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
| Windows | [Installer](https://github.com/luaksone/scoutly-releases/releases/download/v1.12.26/Scoutly-Setup-1.12.26-x64.exe) | 1.12.26 |
| Windows | [Portable application](https://github.com/luaksone/scoutly-releases/releases/download/v1.12.26/Scoutly-Portable-1.12.26-x64.exe) | 1.12.26 |
| Android | [APK](https://github.com/luaksone/scoutly-releases/releases/download/v1.12.26/Scoutly-Mobile-1.4.26-release.apk) | 1.4.26 |

The Windows installer adds Scoutly to the system normally. The portable build can be run without installation. Android may require permission to install applications from the browser or file manager used to open the APK.

## Data and privacy

Scoutly stores monitoring data locally. Network requests are made to the pages you choose to monitor and, when configured, to the location of your encrypted synchronization file. Scoutly does not require an account.

Website owners may restrict automated requests. You are responsible for configuring reasonable check intervals and using Scoutly in accordance with the terms and applicable rules of each website.

## Verifying downloads

SHA-256 hashes for the current packages are listed in [SHA256SUMS.txt](SHA256SUMS.txt).

On Windows, a downloaded file can be checked with PowerShell:

```powershell
Get-FileHash .\Scoutly-Setup-1.12.26-x64.exe -Algorithm SHA256
```

Compare the reported hash with the corresponding entry in `SHA256SUMS.txt`. Versions 1.12.18 / 1.4.19 also verify future releases against the publisher key embedded in the app and [signed release manifest](scoutly-release-manifest.json).

## License

Scoutly is distributed as freeware under the [Scoutly End User License Agreement](LICENSE). The agreement permits use of the compiled application and restricts reverse engineering, modification, and redistribution.
