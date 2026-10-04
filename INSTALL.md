# Partvision's ReSkate Trainer - 0.4.0 preview 3

Tricks and UI development preview for ReSkate 1.0.6 and Skate Steam build 25414733.

## Install or upgrade

1. Extract the whole ZIP.
2. Close Skate and every ReSkate launcher window.
3. Run `Install.cmd`. If Windows denies access to the Steam folder, run it as administrator.
4. Start ReSkate normally, enter a solo map, and press **Home**.

The installer uses `C:\Program Files (x86)\Steam\steamapps\common\Skate`, verifies the game executable, and backs up your current DLL and launcher to a timestamped folder in `EarlyTrainerBackups` before replacing them. If 0.1 is installed, that working build becomes the backup. Do not install this through the Mods tab: it is a custom ReSkate DLL and matching launcher. Existing game data and Mods folders are not changed.


## Force No Fall

Player now includes **Force No Fall**, using ReSkate's local No Bail protection. The goal is to stay on the board through impacts and bad landings, like the requested Skate 3 behavior. Native hooks filter bail causes (including inline collision/landing causes), impact and animation wipeout requests, direct wipeout state selection, and sensitive body-contact reports. Exact all-impact parity has not been playtested.

Enable it before testing a wall collision, traffic hit, hard landing or failed trick. Recover first if already fallen. Ordinary skating transitions and manually getting off the board remain native. This trainer switch is solo-only; it follows the existing native availability checks.

The switch starts off. Its optional keybind defaults to Unbound; configure Hold or Toggle in **Keybinds and presets**. Values and bindings from previews 1/2 migrate without changing Home, End or existing movement bindings. Settings now use schema 4 and load schema 2/3/4.

**Reset No Fall**, turning the switch off, or **End** restores the native no-bail preference captured before enabling it. A pre-existing native No Bail setting or active noclip can still protect you independently; the UI reports that. Native debug preferences can remain saved if you exit without resetting, so turn the switch off before closing to restore its previous preference.

Automated checks cover ownership, queue retries, quick enable/disable/re-enable while requests are pending, failed restoration requests, restoring pre-existing protection, legacy keybind migration and saved new bindings. The native game behavior has not been playtested for this build.

## Preview 3 fixes

Ground FS Fastplant / boneless tuning:
- Footplant Speed now scales the native Boneless outgoing planar-speed graph and its active FloatCurve. Preview 1 changed different footplant launch fields.
- Footplant Height now scales the Boneless jump-height-versus-planar-speed graph.
- Curve Y coordinates and tangent Y offsets scale together; X coordinates, curve domain and interpolation types stay unchanged.
- Disabling either feature restores its captured fields and curves independently.

These controls target ground fastplants, including the reported ground FS Fastplant. They do not speed up the animation. Compare on level ground at the same nonzero approach speed. Start with one control at 2x, restore it, then test the other. Gameplay effects still need an in-game playtest of this build.

Right-click any trainer movement slider to open a number editor. Enter commits; Apply also commits; Cancel or Escape discards the draft. Invalid, non-finite and out-of-range entries do not apply.

| Control | Drag range | Manual range |
| --- | --- | --- |
| Ground fastplant / body flip / body spin factors | 0.25-3x | 0.25-1000x |
| Ollie Power | 0.25-10x | 0.25-1000x |
| Off-board Jump factor | 0.25-5x | 0.25-20x |
| Boost cutoff | 5-150 m/s | 5-1000 m/s |

Custom values remain visible and survive redraw, saving, relaunch and preset loading. Native boost/slingshot bounds, UI scale and time-scale bounds retain their existing limits. Noclip uses its supported speed presets. Freecam FOV and engine render-distance editors retain their existing controls.

Other 0.4 controls: experimental Infinite Footplanting (pop-decay removal), Allow Multiple Body Flips, Body Flip Speed, Body Spin Speed, one-shot Slingshot, Home UI scale, individual feature resets and OVERRIDE indicators. Infinite chaining and native trick effects remain unverified. New trick bindings default to unbound; configure Hold/Toggle under Keybinds and presets. Player overrides remain solo-only.

Automated checks: 149 mapped fields plus the active ground-speed curve; exact individual/full reset; fresh baseline capture for fields and curves; unrelated-byte and unrelated-curve preservation; curve domain/X/type preservation; unsupported mapping rejection; custom number persistence; real ImGui right-click/text/Enter interaction, invalid-entry rejection and Escape cancel; six pages at 75/100/150% scale. Runtime and launcher compile in Windows x64 Release. In-game playtest: not run.

Remaining 0.4: Off-Board Speed, verified Off-Board Jump Height, Air Control, Gravity Multiplier, board-flip behavior, broader reset coverage, controller bindings and in-game regression testing.

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

**Ollie Power:** 0.25–10x tuning strength. The earlier 0.1 slider did not represent a true height multiplier; this is now labelled accurately. Both minimum and maximum ollie-height-versus-speed graphs are scaled. Reset restores the captured pre-trainer values. Measure comparable flat-ground jumps at the same speed using the last-jump readout. It can affect other tricks that use the same pop graphs.

**Slow motion:** 0.10–1.00x simulation time using ReSkate's existing named setting. The applied scale/status is shown. Disabling restores the captured prior time scale. Session changes also use ReSkate's existing multiplayer setting rules.

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

- ReSkate 1.0.6: https://github.com/Dingo-Shenanigans/ReSkate — base commit `f815658bf1833ef0580fc87ea1758bfd91ddb361`.
- Andrew Nakas's ReSkate Trainer: https://github.com/andrewnakas/reskate-trainer — physics name/access helpers, state observation and off-board velocity helpers adapted from commit `013d131c692d009bf118bd788a583345f6abbaa4`.
- Dear ImGui supplies the UI renderer.

GPL-3.0; see LICENSE. Complete corresponding source and `BUILD-PARTVISION.md` are included in `Partvision-ReSkate-Trainer-0.4-preview2-source.zip`.
