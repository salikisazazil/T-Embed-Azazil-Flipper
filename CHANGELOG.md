# Release notes

## r4 packaging / WebStrike 1.0.2 — 2026-10-22

- Consolidate current SD/source downloads; include terminal and HTTP streaming fixes.
- Add verified app-only r4 BIN for Launcher, retaining the full USB image.
- Keep BW16 companion firmware and one current download/checksum table.
- Installation/boot on physical Launcher hardware remains untested.

## 2.0.0-azazil-r4 — 2026-10-22

- Repair deep-sleep entry: clear inherited wake sources, gate automatic light sleep, debounce encoder release and use an internal-RAM shutdown task.
- Add Azazil WebStrike 1.0 and eight required network/TLS API exports.
- Preserve the full r3 SD pack and add WebStrike: 33 FAPs total.
- Include full source, matched firmware/SD, checksums and validation evidence.
- Build and host tests pass; physical hardware acceptance remains pending. See [r4 details](R4.md).

## 2.0.0-azazil-r3 — 2026-10-21

- Named the distribution and firmware identity **T-Embed-Azazil-Flipper**.
- Built the cc1101-plus firmware and seven matching custom apps from one source tree.
- Included ProtoPirate **4.1-r3**, Welcome enabled, with all **36** matching plugins and required resources.
- Retained r2 rotary editing, Receive layout, Remote Analyzer and bounded-history improvements.
- Included r2 audio-worker scheduling and allocation handling changes; hardware confirmation of the reported sound crash is pending.
- Added previously missing BW16 I2C, Wardriver Plus, WDGWars Map, RTL433, WIFITE and Walkie Talkie FAPs to the full SD pack.
- Added a source archive, single merged BIN, full SD archive, SHA-256 checksums, build logs and exact app/file inventories.

This release does not add Bruce, Momentum or Doctor firmware integration. It does not change the RF protocol algorithms as part of rebranding.
