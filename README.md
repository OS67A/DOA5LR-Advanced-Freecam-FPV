# DOA5LR Freecam & First-Person Mod


## 1.0.3 Features

- First-person FOV is **80 degrees vertically** (about **112.3 degrees horizontally** at 16:9).
- While being thrown, first-person view tilts **5 degrees downward relative to the character's head**. Eye position and head tracking are unchanged, and the camera does not lock onto the opponent. The offset eases in and returns smoothly to the normal head-relative angle when the throw ends.

## 1.0.2 Features

- Increased the first-person vertical FOV from **60 to 68 degrees** (about 100 degrees horizontally at 16:9).
- Fixed first-person view unexpectedly reverting to a fixed freecam position when fighter tracking data was briefly unavailable. First-person and orbit modes now hold their last view and resume tracking automatically.

## Installation

Copy both `winmm.dll` and the `DOA5Freecam` folder into the folder containing `game.exe`.

The DLL loads the bundled runtime libraries and camera code directly inside the game.

## Requirements

- 64-bit Windows
- Steam version of DOA5LR 1.10C (32-bit game)

Supported `game.exe` SHA-256:

```text
88d12d42ba49ac696de1acbb25da12615726e8b6259fc24dd6e7d4d939f89bbc
```

The mod will not apply camera changes to an unrecognized executable.

## Controls

Use the **top-row keys**, not the numpad, for the Alt shortcuts. Turn **Num Lock on** for the numpad controls.

| Key | Action |

**Alt + -** (top row): Enable freecam
**Alt + =/+** (top row): Cam reset
**B**: Switch focus between P1 and P2
**V**: Toggle FPV
**Numpad 8 / 2**: Move forward / backward; adjust distance in orbit mode
**Numpad 4 / 6**: Move left / right; orbit left / right in orbit mode
**Numpad 9 / 3**: Move up / down; fine-tune eye height in first-person view
**Numpad 7 / 1**: Rotate horizontally
**Numpad + / -**: Look up / down
**Numpad / or \***: Roll the camera (tilt the view)
**Shift**:  Faster movement

## Features

- Free camera movement and rotation without angle limits. The camera holds its position and orientation when you release the controls.
- Camera controls respond only while the game window is active.
- First-person view follows the character's head position and orientation. When your character performs a throw, the camera looks toward the opponent's upper chest.
- Reduced clipping through character models and stage floors.

## Compatibility with Other Mods

This mod does not replace AutoLink's `DInput8.dll` or ReShade's `d3d9.dll`.

**Do not overwrite an existing `winmm.dll` from another mod.** This release does not support chaining other WinMM proxy DLLs.

If another mod uses numpad shortcuts, disable those shortcuts in that mod to avoid conflicts. This mod does not change third-party mod files or settings.

## Disabling or Uninstalling

To temporarily prevent the mod from loading, create an empty file named `disabled.flag` inside the `DOA5Freecam` folder, then restart the game.

To uninstall, close the game and remove this mod's `winmm.dll` and `DOA5Freecam` folder.

The mod applies changes only in memory. It does not modify `game.exe` or the game's data files. A separate watchdog thread inside the game restores any remaining changes if the camera control thread stops. All in-memory changes are cleared when the game exits.

## Logs

Diagnostic files are saved to:

```text
%LOCALAPPDATA%\DOA5LRFreecam\freecam-<PID>.log
%LOCALAPPDATA%\DOA5LRFreecam\status-<PID>.json
```

`<PID>` is the game's process ID.

The mod does not connect to the network, register itself to run at Windows startup, or launch a separate process.

## Source Code and Licenses

The DLL's C source is included in `DOA5Freecam/source`, and the camera code is in `DOA5Freecam/scripts`.

The bundled Python runtime's license is in `DOA5Freecam/runtime/LICENSE.txt`.
