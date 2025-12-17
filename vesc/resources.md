# Little FOCer V3.1 / VESC resources (2025-03)

Purpose: quick reference for hardware docs, firmware, tools, and reliable guides for the Little FOCer V3.1 (20S, ~84V) and VESC firmware.

Official / manufacturer
- Little FOCer V3.1 product page: https://customwheel.shop/high-voltage-vesc-motor-speed-controllers/little-focer-v31-vesc-84v-20s-chassispanel-mount
- Tronic Systems (designer): https://tronicsystems.com/products/x12 (general VESC info, support)
- VESC Project home: https://vesc-project.com/
- VESC documentation: https://vesc-project.com/documentation
- VESC Tool downloads: https://vesc-project.com/vesc_tool (Mac/Win/Linux installers; version shown in-app under Help → About)

Firmware / hardware target
- Hardware target: Little FOCer uses the VESC “75_300 / LFV3” target (same family as VESC 75/300). Pick this when flashing.
- Stable baseline commonly used on LFV3: firmware 5.02/5.03 (older), 6.05 (newer). Verify compatibility in the VESC forum before flashing newer than 6.05; keep a copy of the previously working firmware in `vesc/firmware/`.
- Upgrade/downgrade tip: after flashing, reconnect, read all settings, and re-run motor detection if the major firmware version changes. Keep known-good motor/app configs exported before flashing.

Setup / how-to (Mac + LFV3)
- Install VESC Tool for macOS from the link above (free tier works for USB). Check version in Help → About; match configs/firmware to that version.
- Connect: power the LFV3 (XT60), USB-C to Mac, select `/dev/tty.usb*` → Connect → Read FW/Hardware.
- Flash: choose hardware 75_300/LFV3 → upload firmware → wait for reboot → reconnect.
- Configure: run motor detection, set voltage/current limits for 20S pack, set RPM limits to protect the controller, then configure App (Balance/UART/PPM). Save motor and app configs to `vesc/configs/` with firmware and date in the filename.
- Logging: use VESC Tool RT Data to capture CSVs for tuning; store in `vesc/logs/` with notes on battery voltage, load, and terrain.

Community guides / references
- Balance App info (VESC site): https://vesc-project.com/node/2689
- VESC Balance Telegram group: https://t.me/joinchat/JP0KNxbguWM5KhHrT5_CYA
- VESC Tool setup video: https://youtu.be/lDuV8cnPRmI
- VESC fault codes list: https://vesc-project.com/node/3941
- rESCue safety project: https://github.com/thankthemaker/rESCue (for fault handling ideas)

What to store here
- Firmware/tool installers (with version and source) in `vesc/firmware/`.
- Exported motor/app configs per firmware in `vesc/configs/` (name them `motor-config_little-focer-v3.1_<fw>_<date>.xml` etc.).
- Pinouts, harness drawings, connector BOM in `vesc/wiring/`.
- RT data, fault logs, screenshots in `vesc/logs/`.

CLI (headless) usage
- Binary: `~/Applications/VESC Tool.app/Contents/MacOS/VESC Tool` (Mac install path you’re using).
- Common commands (add `--offscreen` to avoid UI):
  - `--vescPort <port>`: set serial port (e.g., `/dev/tty.usbmodemXXXX` or `/dev/tty.SLAB_USBtoUART`).
  - `--getMcConf <file>` / `--setMcConf <file>`: read/write motor config XML.
  - `--getAppConf <file>` / `--setAppConf <file>`: read/write app config XML.
  - `--queryDeviceFwParams`: print HW/FW info.
  - `--debugOutFile <file>`: log debug output.
Examples:
```bash
~/Applications/VESC\ Tool.app/Contents/MacOS/VESC\ Tool \
  --offscreen --vescPort /dev/tty.usbmodemXXXX \
  --getMcConf vesc/configs/motor-config_little-focer-v3.1_6.05_16s_16in.xml

~/Applications/VESC\ Tool.app/Contents/MacOS/VESC\ Tool \
  --offscreen --vescPort /dev/tty.usbmodemXXXX \
  --getAppConf vesc/configs/app-config_balance_6.05_16s_16in.xml

~/Applications/VESC\ Tool.app/Contents/MacOS/VESC\ Tool \
  --offscreen --vescPort /dev/tty.usbmodemXXXX \
  --queryDeviceFwParams
```
Use the port that appears when the LF is connected (`ls /dev/tty.* /dev/cu.*`).

Balance PID tuning notes (2025-12) for 16S, 16" wheel, Little FOCer V3.1, FW 6.05
- IMU: oscillation (~4–5 Hz) on stand was fixed by setting IMU profile to “Balance Unicycle” (was Default).
- Wheel: set `si_wheel_diameter` to 0.406 m for 16".
- Typical community ranges: Angle P 0.8–1.5, Angle D 0.1–0.6 (higher if filtered), Rate P 0.05–0.15, Rate D 0.1–0.25, D LP 5–15 Hz, Loop 500–1000 Hz, I ~0.
- Our tests: high Angle D (up to ~6) reduced sway more than low D. Adding Rate loop damping helps:
  - A workable direction to try: Angle P ~1.0, Angle D 5–6, Rate P ~0.1, Rate D ~0.2, D LP 10–12 Hz (HP 0), Loop 1000 Hz, I=0. If too harsh/noisy, back Angle D toward 4–5 and/or tighten D LP to ~8 Hz; if wobble persists, bump Rate D ≤0.25. If still stubborn, try Loop 500 Hz for phase margin.
  - Lower-gain set that reduced self-oscillation: Angle P ~0.6–1.0, Angle D ~0.1–0.3, Rate P ~0.05–0.1, Rate D ~0.12–0.2, D LP 5–10 Hz.
- Save known-good configs to XML (`vesc/configs/`) once stable.
