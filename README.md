# nfsu2-recompiled-anbernic-h700
Native ARM64 port of Need for Speed: Underground 2 adapted for Anbernic RG34XXSP / RG35XX / RG34XX / RG40XX (Allwinner H700) running muOS &amp; PortMaster.
Need for Speed: Underground 2 — Anbernic RG34XXSP / H700 (muOS) PortMaster Package
Native ARM64 static binary recompilation of Need for Speed: Underground 2, adapted and optimized for Anbernic RG34XXSP and all Allwinner H700 handhelds (RG35XX Plus, RG35XX H, RG35XX SP, RG34XX, RG28XX, RG40XX H/V, RG CubeXX) running muOS, as well as RK3326 handhelds (R36S) on ArkOS / ROCKNIX.
Important Legal Notice: This package contains only the open-source/recompiled launcher, binaries, shader files, artwork, and controller configurations. No copyrighted game assets are included. You must supply your own legitimate retail PC copy of Need for Speed: Underground 2.

What is Fixed & Optimized in This Release
muOS Display & Mali-G31 (fbdev) Direct Rendering:
Fixes the Failed to initialize SDL2: kmsdrm not available crash on muOS (Allwinner H700).
Automatically detects muOS and uses the native libmali OpenGL ES 3.2/2.0 driver instead of forcing kmsdrm/Mesa.
Enables Direct Window Rendering (NFSU2_PRESENT_THREAD=0) on fbdev, eliminating 1 ms black FBO sync flashes at startup/menus and saving ~3–4 ms per frame.
Real-Time Left Stick ⇄ D-Pad Swap (MENU + SELECT & Stickless H700 Support):
Press MENU + SELECT (or SELECT + L3) at any time in-game to swap Left Stick (car steering) and D-Pad (World Map / SMS / Enter Shop / Career stats) on the fly, with instant return-to-center steering when releasing D-Pad Left/Right.
Includes NFSU2_SWAP_DPAD_STICK (0 | 1 | auto) in nfsu2.cfg — in auto mode, stickless H700 devices (RG35XX Plus, RG35XX SP, RG34XX, RG28XX) automatically boot with D-Pad car steering enabled.
3:2 (720×480) Display & UI Alignment:
Properly aligns 2D UI menus and HUD elements on the RG34XXSP 720×480 (3:2) screen (NFSU2_WIDESCREEN=0 by default in nfsu2.cfg; can be set to 1 for 16:9 devices).
Hardware MENU + START & SELECT + START Clean Exit:
Includes an evdev hotkey daemon (tools/exit_watcher.py) that listens to Anbernic muOS-Keys (MENU code 312 + START code 311) and Gamepad (SELECT + START) to cleanly save and exit back to muOS.
Full Anbernic Controller Mapping (Deeplay-keys) + Virtual Keyboard:
Configured gamecontrollerdb.txt for Anbernic H700 controls, including R3 (right stick click) to toggle the built-in on-screen keyboard for profile creation.
1 GB RAM & Atmospheric Distance Fog Optimization (100% Stock Clocks):
Runs at 100% stock system CPU/GPU clocks by default (NFSU2_BOOST_CLOCKS=0) for zero voltage ripple and cool operation.
Uses radial & atmospheric distance fog (NFSU2_FOG=1, NFSU2_DRAW_DIST=155) and balanced graphics preset for locked ~30 FPS in heavy city traffic with ~300 MB RAM free.
Pre-formatted muOS Menu Artwork Included:
Includes MUOS/info/catalogue/External - Ports/ box art (320x240), preview, and game description (also auto-installed on first launch by NFSU2.sh).

Installation Instructions (muOS)
Extract this archive onto the root of your muOS SD card:
NFSU2.sh → /ROMS/Ports/NFSU2.sh
nfsu2/ → /ports/nfsu2/
MUOS/ → /MUOS/ (optional: installs the game cover art in the muOS Ports menu immediately; NFSU2.sh also installs it automatically on first launch)
Copy your legitimate PC Need for Speed: Underground 2 installation files into:
/ports/nfsu2/gamedata/ (The gamedata folder must contain SPEED2.EXE, CARS/, GLOBAL/, TRACKS/, SOUND/, MOVIES/, LANGUAGES/, etc.)
Supported SPEED2.EXE versions (auto-detected on launch):
v1.0 unpacked (4,788,224 bytes, MD5: 95b4dc3e9a6c72b06a8bd62b0c56ea63) — recommended
v1.2 unpacked (4,800,512 bytes, MD5: 6445adbf4e8d64be51e96a69bba168a4)
Launch NFSU2 from the Ports menu on your console!

🌍 How to Change Game Language (nfsu2/nfsu2.cfg)
Open /ports/nfsu2/nfsu2.cfg in any text editor and edit the NFSU2_LANG= line:
NFSU2_LANG=English
1. Official European / Asian Multi-Language Releases
If your gamedata/LANGUAGES/ folder contains multiple .bin language files (French.bin, German.bin, Spanish.bin, Italian.bin, etc.), set NFSU2_LANG to any of the supported values:
NFSU2_LANG=English (or English UK)
NFSU2_LANG=French
NFSU2_LANG=German
NFSU2_LANG=Italian
NFSU2_LANG=Spanish
NFSU2_LANG=Dutch
NFSU2_LANG=Swedish
NFSU2_LANG=Danish
NFSU2_LANG=Japanese
NFSU2_LANG=Korean
NFSU2_LANG=Thai
(Note: For spoken audio/voiceover in French, German, Spanish, or Italian, make sure your gamedata/SOUND/SPEECH/ folder contains the corresponding localized speech files from that language's disc).
2. Russian / Polish / Czech / Community Localizations (1C / SoftClub, etc.)
Official Eastern European and community localizations (such as the official Russian SoftClub text + voiceover release) replace gamedata/LANGUAGES/English.bin and gamedata/SOUND/ directly:
Simply copy the localized LANGUAGES/ and SOUND/ folders into /ports/nfsu2/gamedata/ (overwriting English.bin) and leave NFSU2_LANG=English in nfsu2.cfg.

Controls (Anbernic RG34XXSP / H700)
Button	Driving Action	Menu / Virtual Keyboard
Left Stick (or D-Pad when swapped)	Steer Left / Right	Navigate Menu / Move Keyboard Cursor
D-Pad Up (or Stick Up when swapped)	Enter Shop / Join Race / Event	Navigate Up
D-Pad Down (or Stick Down when swapped)	Career Status / Stats	Navigate Down
D-Pad Left / Right (or Stick L/R)	World Map / Read SMS	Navigate Left / Right
B (South)	Accelerate (Gas)	Confirm / Enter / Type Key
Y (West)	Brake / Reverse	Space (Menu) / Backspace (Keyboard)
A (East)	Handbrake (E-Brake)	Cancel / Back (ESC)
X (North)	Change Camera View	Toggle Upper/Lower Case (ABC/abc)
R1	Nitrous (N2O)	Page Down
L1	Look Behind	Page Up
R2 / L2	Shift Up / Shift Down	Next / Prev Submenu Tab
R3 (Right Stick Click)	Open / Close Virtual Keyboard	Open / Close Virtual Keyboard
MENU + SELECT (or Select + L3)	Swap Left Stick ⇄ D-Pad (Live)	Swap Left Stick ⇄ D-Pad (Live)
Select + R3	Toggle FPS Counter	Toggle FPS Counter
MENU + START (or Select + Start)	Quit Game cleanly to muOS	Quit Game cleanly to muOS

Configuration (nfsu2/nfsu2.cfg)
You can customize performance, controls, and visuals by editing /ports/nfsu2/nfsu2.cfg:
NFSU2_GRAPHICS=balanced (performance | balanced | quality)
NFSU2_FPS=30 (30 or 60)
NFSU2_DRAW_DIST=155 (Draw distance in meters; 155 is optimal for 30 FPS with smooth fog fade)
NFSU2_FOG=1 (1 = atmospheric & radial distance fog enabled, 0 = disabled)
NFSU2_PRESENT_THREAD=0 (0 = direct window rendering without FBO flicker on Mali-G31 fbdev)
NFSU2_WIDESCREEN=0 (0 = aligned 3:2/4:3 UI for 720×480; 1 = 16:9 widescreen patch)
NFSU2_SWAP_DPAD_STICK=0 (0 = normal, 1 = start with D-Pad steering, auto = auto-enable on stickless handhelds)
NFSU2_SWAP_HOTKEY=1 (1 = enable MENU + SELECT / SELECT + L3 live swap hotkey, 0 = disable)
NFSU2_BOOST_CLOCKS=0 (0 = keep 100% stock console CPU/GPU clocks, 1 = force performance governor)

Credits & Acknowledgments
codepdbh/nfsu2-recompiled — Original x86-to-C static recompilation of Need for Speed: Underground 2.
manuelpllull/nfsu2-recompiled-r36s — ARM64 OpenGL ES 2.0 renderer port and R36S adaptation.
ThirteenAG — Widescreen Fix HUD layout tables (MIT).
