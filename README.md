<div align="center">

# T-Embed-Azazil-Flipper

**A matched firmware + SD toolkit for LilyGo T-Embed CC1101 Plus**

ESP32-S3 · CC1101 · Rotary controls · BW16 over I2C

[Download release](../../releases/latest) · [Install guide](docs/INSTALL.md) · [All apps](docs/APPS.md) · [Changes](CHANGELOG.md)

</div>

---

This is Azazil's custom **SOR3NT-based ESP32 port**, packaged with its matching applications and resources. It brings our native RF, wireless survey and companion-board tools into one reproducible release, with the latest ProtoPirate 4.1-r3 update.

**Target:** LilyGo T-Embed CC1101 **Plus**, ESP32-S3, 16 MB flash and octal PSRAM. This image is not for a Flipper Zero STM32, ESP32-C5, Momentum or Bruce. “WirelessPi” was the earlier build name; no Raspberry Pi is required.

## Current downloads

The current package is **r4 firmware + WebStrike 1.0.2**. WebStrike includes automatic terminal scrolling, clear-on-new-scan, and streaming HTTP checks beyond the old 16 KiB cutoff. Deep-sleep fixes are in r4. Build/host tests pass; physical-device acceptance remains pending.

Choose files from [the latest release](../../releases/latest):

| File | Use |
| --- | --- |
| `T-Embed-Azazil-r4-CC1101-Plus-Launcher-App.bin` | Install from bmorcelli Launcher's SD browser; 3.43 MiB app, fits a 4 MiB slot. **Never flash at 0x0.** |
| `T-Embed-Azazil-Flipper-2.0.0-r4-CC1101-Plus.bin` | Full USB-flash image at **0x0**, 16 MB / DIO / 80 MHz. |
| `T-Embed-Azazil-SD-r4-WebStrike-1.0.2.zip` | Complete current SD pack, including WebStrike 1.0.2; no separate patch needed. |
| `T-Embed-Azazil-Source-r4-WebStrike-1.0.2.zip` | Full firmware/app source, current tests and validation records. |
| `BW16-I2C-4.5-Azazil-Companion.zip` | Separate BW16 companion firmware, uploader and source; see [BW16 guide](BW16.md). |
| `SHA256SUMS-current.txt` | Checksums for the five downloads above. |

Keep your existing SD data. If you already have the r4 pack, only replace `apps/Tools/azazil_webstrike.fap` from the current SD ZIP. Use Launcher for future firmware installs when running under Launcher; Azazil's own OTA updater selects another OTA slot independently.

The app-only BIN is byte-identical to the app in the merged r4 image; its checksum and SHA-256 trailer pass. The exact reported Launcher error/version was unavailable, and hardware installation is untested. See [installation](docs/INSTALL.md) and [release details](R4.md).

GitHub's automatic Source code archives contain this distribution repository. Use the explicitly named complete Source ZIP above.

## Apps added to this build

| Application | Version | What it provides | Requirements / limits |
| --- | --- | --- | --- |
| **Azazil WebStrike** | **1.0.2** | Fifteen lightweight web-testing modules, shared target, Quick Audit and reports. | Requires r4 API; original bounded implementations, not desktop ports. |
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

Extract the explicitly named complete Source asset and run `bash build_webstrike.sh` with ESP-IDF activated. Current validation logs and tests are included in the complete Source ZIP. BW16 companion source remains under `firmware/bw16_controller_i2c/` and is flashed separately.

## Credits and licensing

Based on [SOR3NT's Flipper-Zero-ESP32-Port](https://github.com/Sor3nt/Flipper-Zero-ESP32-Port), with the custom Native Tools work from [salikisazazil/Flipper-Zero-ESP32-Port](https://github.com/salikisazazil/Flipper-Zero-ESP32-Port), base commit `10c2fbe4d039b05165213fb29fdbc658f0b57072`. SD resources originate from SOR3NT's v2.0.0 pack, updated with the matching custom FAPs and ProtoPirate resources.

ProtoPirate, rtl_433, Flipper contributors and the individual app/library authors retain their respective credits and licenses. Original notices remain in the source archive; this distribution does not relicense third-party code. See [NOTICE](NOTICE.md). Use radio and network tools only on equipment and networks you are authorized to test.
