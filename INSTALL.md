# Partvision's ReSkate Trainer â€” 0.4.0 preview 1

Tricks and UI development preview for ReSkate 1.0.6 and Skate Steam build 25414733.

## Install or upgrade

1. Extract the whole ZIP.
2. Close Skate and every ReSkate launcher window.
3. Run `Install.cmd`. If Windows denies access to the Steam folder, run it as administrator.
4. Start ReSkate normally, enter a solo map, and press **Home**.

The installer uses `C:\Program Files (x86)\Steam\steamapps\common\Skate`, verifies the game executable, and backs up your current DLL and launcher to a timestamped folder in `EarlyTrainerBackups` before replacing them. If 0.1 is installed, that working build becomes the backup. Do not install this through the Mods tab: it is a custom ReSkate DLL and matching launcher. Existing game data and Mods folders are not changed.


## 0.4 preview 1 — new controls

This starts 0.4; it does not complete every item in the milestone.

Player > 0.4 Tricks:
- Footplant Speed: scales standstill launch speed and launch speed limit, 0.25–3x. Animation speed is unchanged.
- Footplant Height: scales upward takeoff velocity, 0.25–3x. This is launch power, not a measured height multiplier.
- Infinite Footplanting (experimental): sets pop-decay multiplier to 1. Infinite chaining is not verified.
- Allow Multiple Body Flips: clears the perfect-body-flips single-rotation constraint. The supported game's default is already off, so enabling it may make no difference. Board kickflips are separate.
- Body Flip Speed: scales flip strength and speed limit, 0.25–3x.
- Body Spin Speed: scales four body-spin response graphs plus auto-spin speed limit, 0.25–3x.

All six use named fields from the supported game's physics asset. Their visible gameplay effects have NOT been verified in-game. Unsupported mappings disable the corresponding control.

Player > Slingshot: one forward and one upward native boost. Forward strength 1–50 m/s, upward strength 1–25 m/s. Solo-only, on-board, UI button only. Requires native boost availability. Reset does not reverse velocity already added.

Home: persisted UI scale 75–150%, player activation count. Player: independent native-value restore buttons and OVERRIDE indicators for new tuning controls. New trick keyboard bindings default to unbound; assign them under Keybinds and presets, including Hold/Toggle. Slingshot and controller bindings remain UI-only/pending respectively.

Physics ownership now captures each feature's fields independently, restores only those fields, and refreshes the skater cache on a new skater identity. Config schema 3 loads the old schema 2 values and bindings. Presets include new trick values, bindings and UI scale. Enable switches still start off each launch. Flight speed now uses ReSkate's supported presets instead of arbitrary unsupported numbers.

Automated checks: 116 mapped fields in seven groups (including ollie), exact individual/full reset, fresh baseline capture, untouched unrelated bytes, unavailable mapping rejection; config migration/roundtrip and binding conflicts; all six pages at 75/100/150% scale. These checks do not verify native movement after a real respawn or map change.

Remaining 0.4: Off-Board Speed, verified Off-Board Jump Height, Air Control, Gravity Multiplier, board-flip behavior, more modified indicators/reset coverage, controller bindings and in-game regression testing. The earlier off-board jump assistance remains experimental.

Suggested playtest: start in solo on level ground. Try one new tuning control at a time, restore it and compare. Then combine footplant and spin tuning and restore only one. Test emergency reset, respawn and map change. Close and relaunch to confirm values persist while switches start off.

## Previous 0.3 additions

Visual: native freecam toggle, freecam FOV 40-120 (0 restores game FOV), film grain, vignette and chromatic aberration with Default/Off/On choices. Camera requests use ReSkate's existing scheduler; live state and native status are shown. Effects and FOV use ReSkate's saved preferences, separate from player presets.

Performance: live FPS/frame time, capture-and-compare FPS sample, shadow-map switch, and separate detail/short/medium/long/extra-long cull-distance settings. Controls enable only after the engine exposes the setting. Distance edits require Apply; values are native engine units, not a calibrated overall distance multiplier. Restore returns to the value before this trainer first changed that setting this session. Rendering settings are not saved across launches. Shadow maps off does not disable every kind of shading.

Emergency reset restores visual and performance values changed through this trainer in the current session. It does not reset unrelated graphics preferences. Profile graphics changes remain saved if you exit without resetting. Player presets do not include graphics controls. Visual actions currently use the UI; no new visual hotkeys are included.

Local rendering controls are intended for solo and multiplayer. Player overrides remain solo-only. Freecam uses native availability and session rules. Server behavior has not been playtested.

Still planned: anti-aliasing modes, sharpness, sky color, Sword Board, pedestrian/traffic draw distance, gameplay FOV and extension to 140 degrees. Those are not functional switches in this package.

This preview compiled and passed automated UI/config checks; it has NOT been playtested in-game. In particular, visible culling behavior must be checked in the loaded map. A setting accepting a value does not guarantee every object responds to it.

## Default controls

| Key | Action | Default mode |
| --- | --- | --- |
| Home | Open/close trainer | Toggle |
| F6 | Ollie Power | Toggle |
| F7 | Slow motion | Hold |
| F8 | Speed boost | Hold, repeated bursts |
| F9 | Noclip/Fly | Toggle |
| F10 | Experimental off-board jump modifier | Toggle |
| End | Emergency reset | Press |
| Insert | Standard ReSkate menu | Existing launcher binding |

Expand **Keybinds and presets** in any tab to rebind controls and choose hold/toggle modes. Escape cancels recording. Duplicate trainer bindings and known menu, chat, and flight keys are rejected. Other game bindings are not exhaustively checked.

Feature checkboxes provide persistent activation until switched off; a hold key adds temporary activation. With a hold binding, release the key to disable that temporary activation. Emergency reset blocks still-held action keys until released. Hotkeys are suppressed in menus/chat and outside the game. Repeated speed boost pauses while the trainer is open. Emergency reset remains available with the trainer open except while recording a binding or editing text.

## Tabs

- **Home:** current map, solo/hosting/guest status, player count, actual presentation FPS/frame time, position X/Y/Z, trainer version, ReSkate base, game build.
- **Player:** Ollie Power, slow motion, speed boost, noclip/fly, experimental off-board jump modifier, jump measurements, per-feature reset controls.
- **Lobby:** current session and planned lobby tools. No teleport or shared session controls yet.
- **Visual:** freecam, freecam FOV, film grain, vignette and chromatic aberration.
- **Performance:** FPS comparison, shadow maps and category-specific cull distances.
- **Info:** credits, versions, settings location and movement diagnostics. Social links are not configured.

## Feature details

**Ollie Power:** 0.25â€“10x tuning strength. The earlier 0.1 slider did not represent a true height multiplier; this is now labelled accurately. Both minimum and maximum ollie-height-versus-speed graphs are scaled. Reset restores the captured pre-trainer values. Measure comparable flat-ground jumps at the same speed using the last-jump readout. It can affect other tricks that use the same pop graphs.

**Slow motion:** 0.10â€“1.00x simulation time using ReSkate's existing named setting. The applied scale/status is shown. Disabling restores the captured prior time scale. Session changes also use ReSkate's existing multiplayer setting rules.

**Speed boost:** configurable burst strength and speed cutoff. Held/toggled boost repeats every 0.3 seconds; Single burst fires once. Uses ReSkate's on-board forward boost. Cutoff uses wall-clock position samples and is not a strict maximum-speed limiter, particularly during slow motion.

**Noclip/Fly:** uses ReSkate's native flight implementation and its checks. Close the menu: WASD moves, Q/E changes altitude, Shift boosts. Existing controller flight inputs work. The trainer restores the prior flight-speed setting when it releases its flight override.

**Off-board Jump Height (experimental):** detects upward movement after a stable off-board interval and attempts one native upward-velocity adjustment. Uses the square root of the chosen factor for velocity scaling; this is not a calibrated height multiplier. Slopes and animation can affect detection. Its status and applied-jump count show whether the engine accepted an adjustment. No claim of successful in-game behavior has been made yet.

**Telemetry:** on-board jump height is peak Y minus takeoff Y, independent of time scale. Speeds and airtime use wall-clock samples, so slow motion lowers reported speed and increases airtime. Teleports, changed skaters and long frame gaps reset the current sample. Off-board jumps are not counted as on-board jumps.

## Settings and presets

Values, keybinds and three named preset slots save to:

`%LOCALAPPDATA%\ReSkate\PartvisionTrainer\settings.json`

Changes save shortly after editing. Activation switches are not saved: all features start disabled on each launch. Loading a preset changes values and bindings; enable the features you want. Player overrides in this preview are solo-only. Entering multiplayer clears their activation. Losing game focus disables speed boost, noclip and slow motion.

Emergency reset stops trainer activation, restores captured ollie/time settings, cancels pending jump assistance and releases trainer-owned flight. It does not undo velocity already applied by a burst or reposition the skater. Existing base-game or other mod settings are not globally reset.

## Restore the previous build

Close the game and launcher. Open the timestamped backup directory created by this installation under `EarlyTrainerBackups`, then run its `Restore.ps1` in PowerShell. You can also manually copy its backed-up DLL and launcher back into the Skate folder. Backups are retained.

## Validation and playtest

This build compiled successfully. Automated checks passed for all six tabs with ImGui assertions enabled, settings serialization, invalid settings, binding conflicts, input suppression/rearming, jump measurements, teleport/respawn resets, off-board trigger detection, and height graph scaling against your installed game data. Home and Player layouts were visually inspected using the rendered ImGui draw data.

**This 0.4 preview has not been playtested inside Skate.** The 0.1 menu and ollie change worked in your playtest; the new features still need runtime verification. Start on flat ground: check F6 and the height readout, hold/release F7 and F8, toggle F9 off/on, then try the experimental F10 control. Test End, a respawn, a map change and a session transition before relying on the build.

## Credits, source and license

Created for Partvision; menu and integration developed with OpenAI Codex.

- ReSkate 1.0.6: https://github.com/Dingo-Shenanigans/ReSkate â€” base commit `f815658bf1833ef0580fc87ea1758bfd91ddb361`.
- Andrew Nakas's ReSkate Trainer: https://github.com/andrewnakas/reskate-trainer â€” physics name/access helpers, state observation and off-board velocity helpers adapted from commit `013d131c692d009bf118bd788a583345f6abbaa4`.
- Dear ImGui supplies the UI renderer.

GPL-3.0; see LICENSE. Complete corresponding source and `BUILD-PARTVISION.md` are included in `Partvision-ReSkate-Trainer-0.4-preview1-source.zip`.
