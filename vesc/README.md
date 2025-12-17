# VESC workspace

Working area for VESC electronics (Little FOCer, balance app, etc). Use this folder for configs, firmware packages, wiring notes, and raw logs. Anything meant for the published site can live in `docs/vesc/` and link back here.

Suggested layout
- `configs/` — VESC Tool motor/app exports plus a short note on firmware/tool version and hardware.
- `firmware/` — downloaded firmware/tool installers, note the matching hardware target (e.g., Little FOCer ≈ VESC 75_300/LFV3).
- `wiring/` — pinouts, harness drawings, connector part numbers.
- `logs/` — RT data, fault dumps, CSV captures.
- `scripts/` — helpers for converting/analyzing configs.

Naming for configs
- `motor-config_<hardware>_<fw>_<date>.xml`
- `app-config_<mode>_<fw>_<date>.xml`
Example: `motor-config_little-focer-v3.1_5.02_2025-03-28.xml`.

Mac + Little FOCer quick notes
- Install VESC Tool for macOS from vesc-project.com; match tool/firmware versions.
- Power the ESC, connect USB-C, pick `/dev/tty.usb*` in VESC Tool, connect, verify hardware before flashing.
- Start with the stable firmware noted in `stuff.md` (v5.02 for Little FOCer V3.1); keep a copy in `firmware/` with a README stating source/version.
