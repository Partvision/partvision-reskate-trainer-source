# Partvision's ReSkate Trainer - 0.4.0 preview 4

For ReSkate 1.0.6 and Skate Steam build 25414733. Development preview; new gameplay behavior has not been playtested.

## Install or upgrade

1. Extract the entire ZIP.
2. Close Skate and every ReSkate launcher window.
3. Run `Install.cmd`. If Windows denies access to the Steam folder, run it as administrator.
4. Start ReSkate normally, enter a solo map, and press **Home**.

The installer validates the supported game and package hashes, and backs up your DLL/launcher under `EarlyTrainerBackups`. Default folder: `C:\Program Files (x86)\Steam\steamapps\common\Skate`. This is a custom ReSkate DLL and matching launcher, not a Mods-tab package. `Restore.ps1` restores a selected backup. `Install.ps1 -VerifyOnly` checks compatibility without installing.

## What's new

- Player has **Tricks / Movement / Off-board / Physics** pages. Keybinds and presets are on Home.
- **Off-board Speed:** scales native desired walking/running velocity while grounded; does not multiply accumulated velocity every frame. Drag 0.25-5x; numeric entry up to 20x.
- **Air Control:** adds horizontal acceleration while riding airborne, with WASD or the controller's left stick. Direction follows the skater. Drag 0-30 m/s²; numeric entry up to 100. No added vertical thrust.
- **Gravity Multiplier:** scales local skater movement gravity during the native state update. Drag 0-2x; numeric entry up to 5x. 0 disables that movement gravity, 1 is normal. Shared world gravity, loose objects, and ragdoll physics are unchanged; native animation paths and contacts can still constrain movement.
- **Off-board Jump Height:** now detects native ground-to-falling takeoff and scales its upward speed once. Drag 0.25-5x; numeric entry up to 20x. Animation/trajectory-driven jumps and hippy jumps are not yet supported. The displayed factor is not a measured height guarantee.
- **Force No Fall:** combines native bail-request filtering with 26 landing/collision tuning overrides: bad/upside-down/squashed checks off, impact force/speed/acceleration thresholds raised. Intended for high-speed collisions and darkslide landings; exact behavior needs an in-game test.
- New movement keybinds, individual resets, ARMED/APPLIED indicators and CUSTOM value markers. Schema 5 preserves existing preview 1-3 values/bindings; new switches begin disabled.

## Force No Fall

Find it under **Player > Physics**. Enable before testing. Recover first if already fallen. It preserves ordinary skating transitions and manually getting off the board; it does not turn collisions off.

Reset No Fall or **End** restores the captured landing/collision values and the previous native No Bail preference. A pre-existing native No Bail setting or active noclip can independently protect you. Native preferences may remain saved if you exit without resetting; switch No Fall off before closing to restore its previous preference.

High-speed wall/traffic hits, hard landings and darkslide landings still require gameplay verification. ARMED means protection is requested; APPLIED means the native protection and tuning overrides are active, not that every possible collision was tested.

## Existing controls

**Tricks:** Ollie Power, ground fastplant/boneless speed and height, experimental Infinite Footplanting (pop-decay removal), Allow Multiple Body Flips, Body Flip Speed and Body Spin Speed. Infinite chaining remains unverified. Multiple Body Flips controls the native body-flip constraint, whose supported default is already off; board kickflip repetition is separate and remains pending.

Footplant Speed/Height target ground fastplants, including FS Fastplant. They scale the Boneless outgoing-speed/height graphs and active speed curve. They do not speed up the animation. Compare level-ground launches at the same nonzero approach speed. Reset restores only captured feature values.

**Movement:** repeated/single forward boost, native Noclip/Fly, Slingshot, Slow motion. Boost cutoff uses measured wall-clock speed and is not a hard limiter. Slingshot adds one forward and upward impulse while riding; resetting values cannot undo already-added momentum. Close the menu for native flight controls: WASD, Q/E altitude, Shift boost, or controller.

**Visual:** native freecam, freecam FOV 40-120 (0 restores game FOV), film grain, vignette and chromatic aberration Default/Off/On choices. Effects use saved ReSkate preferences. General gameplay FOV remains planned.

**Performance:** live FPS/frame time, capture-and-compare FPS sample, shadow maps, detail/short/medium/long/extra-long cull distances. Apply writes native engine units; Restore restores the captured value. Rendering distances are session-only. Disabling shadow maps does not remove every type of shading.

**Home:** map/session/FPS/coordinates/version, UI Scale 0.75-1.5x, keybinds and three value presets. **Info:** credits, movement diagnostics and storage status. **Lobby:** planned tools only.

## Numbers, bindings and reset

Right-click trainer sliders for manual entry. Enter or Apply commits; Cancel or Escape discards the draft. Non-finite or out-of-range entries are rejected. Custom numbers survive redraw, saving and preset loading. Ground fastplant/body rotation factors accept 0.25-1000x; Ollie Power 0.25-1000x; boost cutoff 5-1000 m/s. Native impulse, flight and time-scale limits remain unchanged.

| Key | Action | Default mode |
| --- | --- | --- |
| Home | Open/close trainer | Toggle |
| F6 | Ollie Power | Toggle |
| F7 | Slow motion | Hold |
| F8 | Repeated speed boost | Hold |
| F9 | Noclip/Fly | Toggle |
| F10 | Off-board jump modifier | Toggle |
| End | Emergency reset | Press |
| Insert | Standard ReSkate menu | Existing binding |

No Fall, tricks and new movement hotkeys default to Unbound. Configure Hold/Toggle in **Home > Keybinds and presets**. Escape cancels recording. Duplicate/reserved bindings are rejected. Other game bindings are not exhaustively checked. Air steering supports controller input; full controller menu navigation and controller feature bindings remain later work.

Hotkeys pause in menus/chat and outside the game. Hold adds temporary activation; the checkbox stays active until switched off. End clears switches and suppresses still-held keys until release. Movement requests expire when local updates stop; respawns resolve a fresh local owner. Native velocity inputs and gravity restore after each state update, and do not undo a value replaced by a native writer.

Settings/presets: `%LOCALAPPDATA%\ReSkate\PartvisionTrainer\settings.json`. Player values and bindings persist; activation switches start off. Emergency reset restores visual/performance values changed through this trainer during the session. Player presets do not include rendering controls. Exiting without reset can preserve ReSkate's own saved visual preferences.

## Multiplayer and validation

Player physics overrides are solo-only and reset on entering multiplayer. Local visual/rendering controls are intended for multiplayer; freecam follows native availability rules. Server behavior has not been tested.

Windows x64 Release builds and automated checks pass: 175 named tuning fields; exact full/individual restoration; unrelated-byte/curve preservation; No Fall flags/thresholds; current and legacy settings; movement binding conflicts; temporary-input restoration without compounding or clobbering native writes; native jump edges/respawn/gap rejection; air-steering math; all six main tabs and four Player pages at 75/100/150% scale; real right-click numeric entry and invalid/cancel behavior. These are not in-game physics or collision tests. See `validation.txt`.

0.4 is still a development milestone: animation-driven off-board jump support, repeated board flips, verified infinite footplant chaining and gameplay/respawn regression checks remain pending. Camera, visuals, online tools, overlays and full controller UI follow the roadmap.

## Credits and source

Created for Partvision with OpenAI Codex. Based on ReSkate by Dingo-Shenanigans, v1.0.6 / commit f815658bf1833ef0580fc87ea1758bfd91ddb361. Physics/off-board helper adaptations originate from Andrew Nakas's ReSkate Trainer. Dear ImGui and bundled dependencies retain their licenses. GPL-3.0; complete corresponding source is included. See LICENSE and BUILD-PARTVISION.md.
