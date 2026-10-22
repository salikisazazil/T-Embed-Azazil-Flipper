<div align="center">

# T-Embed-Azazil-Flipper

**A matched firmware + SD toolkit for LilyGo T-Embed CC1101 Plus**

ESP32-S3 · CC1101 · Rotary controls · BW16 over I2C

[Download release](../../releases/latest) · [Install guide](docs/INSTALL.md) · [All apps](docs/APPS.md) · [Changes](CHANGELOG.md)

</div>

---

This is Azazil's custom **SOR3NT-based ESP32 port**, packaged with its matching applications and resources. It brings our native RF, wireless survey and companion-board tools into one reproducible release, with the latest ProtoPirate 4.1-r3 update.

**Target:** LilyGo T-Embed CC1101 **Plus**, ESP32-S3, 16 MB flash and octal PSRAM. This image is not for a Flipper Zero STM32, ESP32-C5, Momentum or Bruce. “WirelessPi” was the earlier build name; no Raspberry Pi is required.

## New in r4

Deep-sleep shutdown now clears inherited timer wake-ups, waits for a stable encoder release, and enters sleep on an internal-RAM task. Adds **Azazil WebStrike 1.0** with 15 lightweight web-testing modules. Build and host checks pass; device acceptance is pending. See [r4 details, limits and test checklist](R4.md).

## Get the complete build

Download these three assets from [Releases](../../releases/latest):

| File | Purpose |
| --- | --- |
| `T-Embed-Azazil-Flipper-2.0.0-r4-CC1101-Plus.bin` | One merged firmware image; flash at **0x0** |
| `T-Embed-Azazil-Flipper-SD-2.0.0-r4.zip` | Ready-to-copy SD contents: apps, plugin assets, databases and bundled resources |
| `T-Embed-Azazil-Flipper-Source-2.0.0-r4.zip` | Complete firmware and app source snapshot, licenses, configuration and build tools |

`SHA256SUMS.txt` identifies the exact assets. **GitHub's automatically generated “Source code” ZIP contains this distribution repository; use our explicitly named Source asset for the complete firmware source.**

## Apps added to this build

| Application | Version | What it provides | Requirements / limits |
| --- | --- | --- | --- |
| **ProtoPirate** | **4.1-r3** | Protocol receive/history tools, supported emulation, model database, Remote Analyzer, saved captures and Welcome help. All 36 matching plugins included. | CC1101; SD assets must match the FAP. Protocol availability does not guarantee every remote is supported. |
| **RTL433** | **1.1.8** | OOK/FSK signal decoding with AUTO/ALL/FIXED profiles, structured decoded fields and JSON/CSV/RAW workflows. | CC1101; profile/frequency and supported decoder matter. One radio cannot listen to every frequency simultaneously. |
| **WIFITE** | **0.8.1** | Experimental native WPS testing UI and firmware bridge. | ESP32 Wi-Fi; this is not the full Linux Wifite toolchain and has no claim of universal WPS success. |
| **BW16 I2C** | **4.5** | Companion-board scanning, AP/client views, capture workflows and PCAP output with sequenced, CRC-checked transport. | External BW16 running the matching I2C companion firmware; **not the UART app**. |
| **Wardriver Plus** | **1.5.2** | Wi-Fi/BLE surveys, optional NMEA GPS, WiGLE export and WDG upload. Reserved-pin checks protect the Plus I2C/NRF configuration. | GPS requires a suitable external module and free pins. Upload services require user configuration. |
| **WDGWars Map** | **1.3** | Color maps, GPS/manual location, pan/zoom and four cached offline areas. | Online services require Wi-Fi/configuration; it does not run Wardriver in the background. |
| **Walkie Talkie** | **1.2 experimental** | Receive-only channel monitor, scan, RSSI/squelch and experimental pulse-to-PCM sound. | Onboard CC1101; **no transmit, conventional FM voice demodulation, or CTCSS/DCS decoding**. |

The SD pack also retains **26 inherited app files including the replaced ProtoPirate entry**: games, NFC/RFID utilities, XRemote, Sub-GHz tools and Authenticator. With seven additional custom entries, the release contains **33 FAP files**. See [the exact inventory](docs/APPS.md) for every filename and its status. Inherited applications are not represented as original Azazil work or as newly hardware-tested.

## Latest ProtoPirate improvements

- About now displays **4.1-r3**, and **Welcome** is available from the main menu.
- Configuration uses **click → rotate to edit → click to finish**.
- Receive uses a separate **Config / History / Del** toolbar, with status text on its own row.
- Remote Analyzer has an explicit Back route, corrected RF path selection and ESP32 SPI status handling, and more responsive scan cancellation.
- History is bounded at **20 entries**, with a bounded display-text arena and serialized SD/history operations.
- The firmware audio worker yields between blocks and handles tone-buffer allocation failure. This addresses a likely sound-related watchdog cause; it is not yet a hardware-confirmed crash fix.

## SD layout

Copy the **contents** of the SD ZIP directly to the card root. The directories are named `apps`, **`apps_assets`** and **`apps_data`**—do not rename them to `app_data` or `apps_asset`.

| Location | Contents |
| --- | --- |
| `apps/SubGhz/` | ProtoPirate, RTL433, Walkie Talkie and inherited RF apps |
| `apps/WiFi/` | WIFITE |
| `apps/GPIO/` | BW16 I2C |
| `apps/Tools/` | Wardriver Plus, WDGWars Map and Azazil WebStrike |
| `apps/Games/`, `apps/NFC/`, `apps/Misc/` | Inherited applications |
| `apps_assets/proto_pirate/` | 36 plugins, keystore resources and model database |
| `apps_data/` | Runtime data directories and bundled game resources |

Other supplied folders include `subghz`, `nfc`, `lfrfid`, `infrared`, `ble`, `dolphin`, `webfs` and `u2f`. The [SD file manifest](docs/SD-FILES.txt) records the archive contents. Back up your card and retain personal captures/settings; never format it merely to install an update.

## Build and validation

Firmware identity: **T-Embed-Azazil-Flipper / 2.0.0-azazil-r4**, built with **ESP-IDF 5.4.1**. Firmware, shutdown regression checks, internal-RAM placement and WebStrike's 98 imports against the linked **1,079-entry API table** pass. The seven earlier custom FAPs and 36 ProtoPirate plugins are retained byte-for-byte from r3; they were not rebuilt for r4. No physical board was connected. See [r4 validation and rebuild instructions](R4.md).

Extract the explicitly named complete Source asset and run `bash build_webstrike.sh` with ESP-IDF activated. Earlier build records and app inventories under `validation/` and `docs/` describe r3; r4 adds `apps/Tools/azazil_webstrike.fap`. BW16 companion source remains under `firmware/bw16_controller_i2c/` and is flashed separately.

## Credits and licensing

Based on [SOR3NT's Flipper-Zero-ESP32-Port](https://github.com/Sor3nt/Flipper-Zero-ESP32-Port), with the custom Native Tools work from [salikisazazil/Flipper-Zero-ESP32-Port](https://github.com/salikisazazil/Flipper-Zero-ESP32-Port), base commit `10c2fbe4d039b05165213fb29fdbc658f0b57072`. SD resources originate from SOR3NT's v2.0.0 pack, updated with the matching custom FAPs and ProtoPirate resources.

ProtoPirate, rtl_433, Flipper contributors and the individual app/library authors retain their respective credits and licenses. Original notices remain in the source archive; this distribution does not relicense third-party code. See [NOTICE](NOTICE.md). Use radio and network tools only on equipment and networks you are authorized to test.
