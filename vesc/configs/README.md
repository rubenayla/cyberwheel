# Configs

Store VESC Tool exports here:
- Motor config XML
- App config XML (balance/PPM/UART/etc.)

For each file, note firmware version, VESC Tool version, hardware revision, motor, and date. Keep a short changelog if you iterate.

XML vs C headers
- Use XML for normal backup/restore and sharing with VESC Tool.
- C header exports are only needed if you embed configs into firmware builds. If you’re not compiling custom firmware, skip the C header saves.

Current files (2025-03):
- `vesc_mcconf.xml`: pulled from Little_FOCer_V3_1 running FW 6.05 (BLE). Note: limits are placeholder (e.g., l_max_vin=57V) and app mode is not balance; treat as “pre-cleanup” reference only.
- `vesc_appconf.xml`: pulled from same session; app_to_use=3 (PPM), not balance. Use as reference, not as a good baseline.
