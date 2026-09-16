# Study/Break Timer - Desktop App

> **Disclaimer:** Coded with Claude AI. Take whatever stance you want on AI you want, and you can choose to not use this i get it. But I just wanted to work on a side hobby and i didn't want to go through as much troubleshooting compared to if I wrote it from scratch with my knowledge.

Requires Python 3 with `tkinter` (comes standard on Windows/Mac installs from python.org; on Linux you may need: `sudo apt install python3-tk`)

## Files in this folder

```
study_timer_desktop.py   - the actual app, run this with Python
Run_Study_Timer.bat      - double-click launcher for Windows
Run_Study_Timer.command  - double-click launcher for Mac
Run_Study_Timer.sh       - double-click launcher for Linux
StudyTimer.desktop       - alternate Linux launcher with a proper app icon
session_log.csv          - created automatically the first time you log
                            a session; open it in Excel/Numbers/Sheets
                            any time to see your full history
```

## How to run

### Windows
Double-click `Run_Study_Timer.bat`

If you see `"Python was not found"`: install Python from [python.org](https://python.org), checking **"Add python.exe to PATH"** on the first installer screen, then restart your computer once before trying again.

### Mac
Right-click `Run_Study_Timer.command` → **Open** (first time only, to get past the security warning), then double-click normally after that.

Requires Python from python.org (not just the old Python that ships with macOS) — if the window opens blank, that usually means it's still using the old system Python instead of the new install.

### Linux

**Option A — shell script:**
```bash
chmod +x Run_Study_Timer.sh
```
Then double-click it. Some file managers will ask "Run in Terminal" or "Display" — choose Run.

**Option B — proper app launcher with an icon:**
1. Edit `StudyTimer.desktop` and update the path on the `Exec=` line to match wherever you actually put this folder.
2. ```bash
   chmod +x StudyTimer.desktop
   gio set StudyTimer.desktop metadata::trusted true
   ```
   (the `gio` step is required on GNOME/Cinnamon-based distros like Linux Mint, or double-clicking will just open it as a text file instead of running it)
3. Double-click normally after that.

### Any OS, from a terminal
```bash
python3 study_timer_desktop.py
```

<img width="800" height="431" alt="Test demo" src="https://github.com/user-attachments/assets/3ba3aa9d-1de9-4376-bb33-5c7ffd276e6d" />

## Controls

| Key | Action |
|---|---|
| `A` | Select Study, or toggle play/pause if Study is already active |
| `B` | Select Break, or toggle play/pause if Break is already active |
| `X` | Play/pause the active timer directly |
| `Y` | Open the Reset menu (Just Selected / All Timers / Cancel), followed by a second "Are you sure?" confirmation |
| `Enter` | Open the Finish menu, and confirm choices inside any menu |
| `←` / `→` | Navigate options inside a menu |

## Session logging

Choosing "Yes" at the end of the Finish → Log flow writes a row to `session_log.csv` (timestamp, Study/Break, duration in seconds, and a formatted `HH:MM:SS.CC` string). This file is created automatically next to the script the first time you log something, and is read back in every time you reopen the app so your history persists.
