# VESC USB connection checks (Mac)

Symptoms: VESC Tool “Could not autoconnect” and no `/dev/tty.usb*` port.

Checklist
- Power: ESC must be powered from pack or bench supply (current-limited). LEDs on.
- Cable: use a known data cable (USB-C to USB-A + adapter often more reliable than some C-to-C charge-only cables).
- Port listing: in Terminal, `ls /dev/tty.usb*`. If nothing, macOS is not seeing the USB-serial device.
- Replug: unplug USB, wait 5s, replug. Try a different Mac port.
- Driver: if the board uses CH340, install the WCH macOS driver; CP210x/FTDI usually work with built-in drivers.
- System Info: `system_profiler SPUSBDataType | head -n 120` should show the device under USB if detected (even if no tty appears).
- VESC Tool: Connection tab → select the `/dev/tty.usb*` port manually → Connect (instead of Autoconnect).
- Last resort: try another cable/adapter or another computer to confirm the ESC’s USB interface is alive.

Little FOCer V3.1 (CP2102) specific
- The Little FOCer V3.1 uses a Silicon Labs CP2102 USB-UART; macOS often needs the CP210x VCP driver.
- Download: https://www.silabs.com/developers/usb-to-uart-bridge-vcp-drivers (choose macOS, ARM vs Intel accordingly), install, then reboot.
- After install, port should appear as `/dev/tty.SLAB_USBtoUART` (or `/dev/cu.SLAB_USBtoUART`). Select it manually in VESC Tool.
- macOS approval: During install, you may need to approve a driver extension. In System Settings → Privacy & Security, scroll to “Driver Extensions” and enable `CP210xVCPDriver (com.silabs.cp210x)`. If prompted with “system software from developer Silicon Laboratories Inc. was blocked,” click Allow, then reboot.
- If the port still doesn’t show after reboot: replug USB with the ESC powered, try a different cable/port, then check `ls /dev/tty.SLAB* /dev/cu.SLAB*`. If no match, use `system_profiler SPUSBDataType` to see if macOS sees the device at all. If nothing shows, suspect the cable/port/board.

Cable sensitivity (real-world note)
- The Little FOCer’s USB-C port can be picky about USB 2.0 D+/D– quality/fit. In testing, one high-quality C-to-C cable enumerated reliably as `Serial STM32 /dev/tty.usbmodemXXXX`; another “good” cable worked on iPhone/Mac but would not enumerate the LF. If you see the port only with a specific cable/orientation, mark that cable as the known-good for VESC.
- On one LF, USB only worked in a specific plug orientation (1 of 4 cable/port combos). Likely cause: one side of the LF USB-C receptacle has weak/dirty/bent contacts. Workaround: mark the known-good orientation, avoid movement, and consider leaving a short, snug USB-C pigtail plugged in permanently to reduce wear.
