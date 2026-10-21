# Complete packaged app inventory

These files are actually present in the SD archive. Newly built means compiled and checked against this linked firmware, not a hardware-test guarantee. Inherited apps are supplied from the SOR3NT v2.0.0 SD pack and were not rebuilt in this release.

| App | SD path | Status |
| --- | --- | --- |
| BW16 I2C 4.5 | `apps/GPIO/bw16_r4tkn_i2c.fap` | Newly built |
| asteroids | `apps/Games/asteroids.fap` | Inherited SD app |
| blackjack | `apps/Games/blackjack.fap` | Inherited SD app |
| blackjack_split | `apps/Games/blackjack_split.fap` | Inherited SD app |
| dice_app | `apps/Games/dice_app.fap` | Inherited SD app |
| doom | `apps/Games/doom.fap` | Inherited SD app |
| flipper_pong | `apps/Games/flipper_pong.fap` | Inherited SD app |
| flipperzero_slots | `apps/Games/flipperzero_slots.fap` | Inherited SD app |
| snake20 | `apps/Games/snake20.fap` | Inherited SD app |
| t_embed_snake | `apps/Games/t_embed_snake.fap` | Inherited SD app |
| tetris | `apps/Games/tetris.fap` | Inherited SD app |
| wolf3d | `apps/Games/wolf3d.fap` | Inherited SD app |
| findmy | `apps/Misc/findmy.fap` | Inherited SD app |
| key_copier | `apps/Misc/key_copier.fap` | Inherited SD app |
| totp | `apps/Misc/totp.fap` | Inherited SD app |
| nfc_rfid_detector | `apps/NFC/nfc_rfid_detector.fap` | Inherited SD app |
| passy | `apps/NFC/passy.fap` | Inherited SD app |
| pocsag_pager | `apps/SubGhz/pocsag_pager.fap` | Inherited SD app |
| ProtoPirate 4.1-r3 | `apps/SubGhz/proto_pirate.fap` | Newly built |
| RTL433 1.1.8 | `apps/SubGhz/rtl433.fap` | Newly built |
| spectrum_analyzer | `apps/SubGhz/spectrum_analyzer.fap` | Inherited SD app |
| sub_analyzer | `apps/SubGhz/sub_analyzer.fap` | Inherited SD app |
| Walkie Talkie 1.2 | `apps/SubGhz/walkie_talkie.fap` | Newly built |
| weather_station | `apps/SubGhz/weather_station.fap` | Inherited SD app |
| wmbuster | `apps/SubGhz/wmbuster.fap` | Inherited SD app |
| Wardriver Plus 1.5.2 | `apps/Tools/wardriver.fap` | Newly built |
| WDGWars Map 1.3 | `apps/Tools/wdgwars_map.fap` | Newly built |
| WIFITE 0.8.1 | `apps/WiFi/wifite.fap` | Newly built |
| flipper_xremote | `apps/flipper_xremote.fap` | Inherited SD app |
| fz_nrf24_jammer | `apps/fz_nrf24_jammer.fap` | Inherited SD app |
| rfid2_reader | `apps/rfid2_reader.fap` | Inherited SD app |
| tagtinker | `apps/tagtinker.fap` | Inherited SD app |

## ProtoPirate plugins

All **36** matching `.fal` files are included in `apps_assets/proto_pirate/plugins/`, including Welcome, About, Configuration, Remote Analyzer, saved-file views and protocol plugins. They are components of ProtoPirate, not 36 separate apps.

## Source-only apps and variants

The full source snapshot also retains upstream apps and alternate variants. This is not a claim that their FAPs are installed.

| Name | Source directory |
| --- | --- |
| FindMy Flipper | `applications_user/FindMyFlipper/FindMyFlipper` |
| TagTinker | `applications_user/TagTinker-main` |
| Asteroids | `applications_user/asteroids` |
| Blackjack | `applications_user/blackjack` |
| Blackjack Split | `applications_user/blackjack_split` |
| BW16 R4TKN | `applications_user/bw16_r4tkn` |
| BW16 I2C | `applications_user/bw16_r4tkn_i2c` |
| Dice D&D | `applications_user/dice` |
| Authenticator | `applications_user/flipper-zero_authenticator/totp` |
| XRemote | `applications_user/flipper_xremote` |
| Game 15 | `applications_user/game15` |
| Mifare Fuzzer | `applications_user/mifare_fuzzer` |
| nRF24 Jammer | `applications_user/nRF24_jammer` |
| NFC Magic | `applications_user/nfc_magic` |
| RFID detector | `applications_user/nfc_rfid_detector` |
| Pong | `applications_user/pong` |
| ProtoPirate | `applications_user/protopirate` |
| Reverse Shell | `applications_user/reverse_shell` |
| RFID2 Reader | `applications_user/rfid2_reader` |
| Roulette | `applications_user/roulette` |
| RTL433 | `applications_user/rtl433` |
| Snake 2.0 | `applications_user/snake20` |
| Snake | `applications_user/t_embed_snake` |
| Tamagotchi | `applications_user/tamagotchi_p1` |
| Tetris | `applications_user/tetris` |
| Texas Holdem | `applications_user/texas_holdem` |
| Walkie Talkie | `applications_user/walkie_talkie` |
| Wardriver | `applications_user/wardriver` |
| Wardriver Plus | `applications_user/wardriver_plus_i2c` |
| WDGWars Map | `applications_user/wdgwars_map` |
| Weather Station | `applications_user/weather_station` |
| WIFITE | `applications_user/wifite` |
| wM-Buster | `applications_user/wmbuster` |
