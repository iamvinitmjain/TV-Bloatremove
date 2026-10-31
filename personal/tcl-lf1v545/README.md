# My TCL LF1V545 home screen

**Summary:** Glass/Cinematic look with 4 dock apps (TV → HDMI 1, Netflix, Prime Video, JioHotstar),
a "Good evening, Vinit" greeting with the clock, and the TV opening on Home at power-on.

| Choice | Setting |
|---|---|
| Look | Glass / Cinematic (navy wallpaper, frosted-glass dock, icon-only buttons) |
| Dock | 4 apps: **TV (HDMI 1)** · Netflix · Prime Video · JioHotstar |
| Header | Greeting with name + large clock + date |
| Power-on | Home (`power_on_home_always`) |

## Fill in after connecting to the TV (192.168.1.8)
Two values in `config.json` have to be read from the TV itself:
1. **HDMI 1 input id**: `adb shell dumpsys tv_input | grep -i hdmi` → replace `REPLACE_WITH_HDMI1_INPUT_ID`
   (looks like `com.tcl.tvinput/.passthroughinput.TvPassThroughService/HW…`).
2. **Package names**: `adb shell pm list packages | grep -i -E "tcl.tv|hotstar|amazon|netflix"`. The
   TV app is assumed to be `com.tcl.tv` and JioHotstar `in.startv.hotstar`; fix them if they differ.

## Push it
```bash
TV_HOST=192.168.1.8 tools/theme.sh personal/tcl-lf1v545
```
The wallpaper is the `glass` theme's own picture. `tools/theme.sh --reset` undoes the theme.
