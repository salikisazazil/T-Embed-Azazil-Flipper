# Installation — T-Embed CC1101 Plus

## 1. Back up

Back up the SD card and device settings. This merged image contains the bootloader, partition table, firmware and OTA initialization. Writing it at 0x0 also overwrites the intervening NVS/settings region. Wi-Fi/settings may need to be configured again.

## 2. Flash the single BIN

Use `T-Embed-Azazil-Flipper-2.0.0-r3-CC1101-Plus.bin` from this release.

- Chip: **ESP32-S3**
- Address: **0x0**
- Flash size: **16 MB**
- Flash mode: **DIO**
- Flash frequency: **80 MHz**

For a serial/web ESP flasher, connect the T-Embed with a data-capable USB cable, select its serial port, select this BIN and set address 0x0. If connection fails, put the board in its documented bootloader mode and retry. Do not place this merged image into an app-only OTA slot; launcher compatibility is not claimed.

With the ESP-IDF environment active, replace PORT with your actual serial port:

```sh
python -m esptool --chip esp32s3 --port PORT --baud 460800 write_flash --flash_mode dio --flash_freq 80m --flash_size 16MB 0x0 T-Embed-Azazil-Flipper-2.0.0-r3-CC1101-Plus.bin
```

## 3. Install SD contents

1. Extract `T-Embed-Azazil-Flipper-SD-2.0.0-r3.zip`.
2. Copy its contents to the FAT32 SD root. `apps/` must be directly on the card, not inside another SD or release folder.
3. Back up and replace the old `apps_assets/proto_pirate/` folder completely. Do not mix plugin versions.
4. Replace the bundled FAP files with their matching release versions. Retain personal files and app settings.
5. Eject the card safely, insert it and restart the device.

The pack contains `apps`, `apps_assets`, `apps_data` and the shared resource folders. Apps create their runtime settings/capture files as needed. No personal API keys, Wi-Fi credentials or user captures are supplied.

## 4. Check the update

- Firmware About: **T-Embed-Azazil-Flipper**, version **2.0.0-azazil-r3**.
- ProtoPirate About: **4.1-r3**. Main menu includes **Welcome**.
- ProtoPirate settings: click once to edit, rotate, click to finish.
- Receive: rotate between Config, History and Del, then click.
- Back should leave Remote Analyzer. Test sound and repeated captures on your board.

The Welcome-only FAP update did not require firmware changes. This branded release includes the previous r2 audio-driver fix, which does require the matching firmware.

## BW16 and GPS

BW16 uses **I2C**, address **0x42**, on this Plus profile:

| T-Embed Plus | BW16 |
| --- | --- |
| GPIO8 / SDA | PA26 |
| GPIO18 / SCL | PA25 |
| 3V3 | 3V3 |
| GND | GND |

Use the matching BW16 I2C companion firmware source supplied in the source archive. The T-Embed BIN does not flash the BW16. Wardriver Plus protects GPIO8/18 and GPIO43/44 from GPS assignment in the shared I2C/NRF configuration. Consult `docs/BW16_PLUS_I2C.md` in the source archive before wiring peripherals.
