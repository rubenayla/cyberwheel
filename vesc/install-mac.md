# Install VESC Tool on macOS (tested 2025-03)

Downloaded file: `~/Downloads/vesc_tool_mac.zip` (contains `VESC Tool.dmg`).

Steps
1) Unzip if needed:
   ```bash
   cd ~/Downloads
   unzip -n vesc_tool_mac.zip
   ```
2) Mount the DMG:
   ```bash
   hdiutil attach "VESC Tool.dmg"
   # mounts as /Volumes/VESC\ Tool\ 1
   ```
3) Copy to user Applications (no sudo needed):
   ```bash
   mkdir -p ~/Applications
   cp -R "/Volumes/VESC Tool 1/VESC Tool.app" ~/Applications/
   ```
4) Clear quarantine/lock flags and ensure writable:
   ```bash
   xattr -dr com.apple.quarantine ~/Applications/VESC\ Tool.app
   chflags -R nouchg ~/Applications/VESC\ Tool.app
   chmod -R u+rwX ~/Applications/VESC\ Tool.app
   ```
5) Eject the DMG:
   ```bash
   hdiutil detach "/Volumes/VESC Tool 1"
   ```
6) Launch (and pass Gatekeeper prompt):
   ```bash
   open ~/Applications/VESC\ Tool.app
   ```

Optional: move to system `/Applications` via Finder drag-and-drop (enter your Mac password) after clearing quarantine. Then launch with:
```bash
open /Applications/VESC\ Tool.app
```
