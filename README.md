# Scoutly — Web Monitoring & Price Tracking Application

[![Platform - Windows](https://img.shields.io/badge/Platform-Windows-0078D6?logo=windows&logoColor=white)](https://github.com/luaksone/scoutly-releases/releases)
[![Platform - Android](https://img.shields.io/badge/Platform-Android-3DDC84?logo=android&logoColor=white)](https://github.com/luaksone/scoutly-releases/releases)
[![License - Freeware EULA](https://img.shields.io/badge/License-Freeware_EULA-blue.svg)](LICENSE)
[![Latest Desktop Release](https://img.shields.io/badge/Desktop-v1.12.0-purple.svg)](https://github.com/luaksone/scoutly-releases/releases/latest)
[![Latest Android Release](https://img.shields.io/badge/Android-v1.3.0-green.svg)](https://github.com/luaksone/scoutly-releases/releases/latest)

**Scoutly** is a fast, local-first web scraper and price tracking application built for **Windows Desktop** and **Android**. It automatically monitors product prices, site content, stock availability, and multi-site comparisons, sending real-time notifications whenever values change.

---

## 🚀 Download Official Binaries

The compiled executables and packages for Windows and Android are available under [GitHub Releases](https://github.com/luaksone/scoutly-releases/releases).

| Platform | Package | Version | Download |
| :--- | :--- | :--- | :--- |
| **Windows Desktop** | Installer (`.exe`) | **v1.12.0** | [Download Setup](https://github.com/luaksone/scoutly-releases/releases/download/v1.12.0/Scoutly-Setup-1.12.0-x64.exe) |
| **Windows Desktop** | Portable (`.exe`) | **v1.12.0** | [Download Portable](https://github.com/luaksone/scoutly-releases/releases/download/v1.12.0/Scoutly-Portable-1.12.0-x64.exe) |
| **Android Mobile** | Debug APK (`.apk`) | **v1.3.0** | [Download APK](https://github.com/luaksone/scoutly-releases/releases/download/v1.3.0/Scoutly-Mobile-1.3.0-debug.apk) |

---

## ✨ Key Features

- 🛒 **Automatic Price & Unit Price Extraction**: Inteligently separates total item prices (e.g. `15,99 €`) from unit/per-piece prices (`0,20 € / kpl`) with full support for store formats such as Tokmanni, Amazon, eBay, and regional retailers.
- 📊 **Interactive Value Charts & Direct Entry Removal**: View historic price trends over hourly, daily, or monthly intervals. Remove erroneous page observations directly from the chart or history table.
- 📉 **Clean Percentage Trends**: Clear trend indicators with precise 1-decimal rounding (e.g., `+1.5%`, `-2.3%`).
- 🔔 **Cross-Platform Notifications**: Real-time alerts on Desktop and Android system notifications (heads-up alerts with high importance and status bar icons).
- 🌐 **Multi-Site Comparison**: Track multiple product listings simultaneously and compare latest values across sites.
- 🔒 **Local-First & Private**: Data remains stored locally on your device with optional encrypted workspace synchronization.

---

## 🔒 Verification & SHA-256 Checksums

To verify the integrity of your downloaded binaries:

```
37FCC7842C0CAF5E1CFCE8B7B7D810B7FE009B0E55CCCA510A049C3ACC775761  Scoutly-Setup-1.12.0-x64.exe
A08DEBB190648D4387DB2834176A37E6D987509D3AD10A0DC77EB371B3D98162  Scoutly-Portable-1.12.0-x64.exe
9AA754858F271675BDB884D8974DDA0AB0763DD0EC49F4C3D38DAF126FB89592  Scoutly-Mobile-1.3.0-debug.apk
```

Verification command on Windows PowerShell:
```powershell
Get-FileHash Scoutly-Setup-1.12.0-x64.exe
```

---

## 📜 License & Usage Terms

Scoutly is distributed as **Freeware** under the terms of the **Scoutly End User License Agreement (EULA)**.

- **Free for Personal & Commercial Use**: You are free to download and use Scoutly without charge.
- **Restrictions**: Decompilation, reverse engineering, unauthorized modification, patching, re-bundling, or redistributing modified versions under another name is strictly prohibited.

For complete terms, read the [LICENSE](LICENSE) file.
