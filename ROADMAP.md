# Partvision's Reskate Trainer Roadmap

| Release | Scope | What must work before moving on |
|---|---|---|
| **0.4 — Tricks & Movement** | Footplant Speed, Footplant Height, Infinite Footplanting, Allow Multiple Flips, Slingshot, Off-Board Speed, Off-Board Jump Height, Air Control, Gravity Multiplier, Spin Speed, Flip Speed | Reliable resets, sensible limits, no broken movement after respawns, settings persist correctly |
| **0.4 — Misc Improvements** | UI Scale, improved modified-value indicators, individual-setting reset controls | UI remains readable at different resolutions and scales, modified settings are easy to identify |
| **0.5 — Camera & FOV** | Controller Freecam, improved Freecam controls, On-Board FOV, Off-Board FOV, Camera Distance, Camera Height, Camera Follow Strength, Camera Smoothing, Camera Roll, Camera Collision toggle, Orbit Camera | Smooth controller input, proper deadzones, reliable camera restoration, no camera lockups |
| **0.6 — Visuals & Performance** | Motion Blur, Depth of Field, Bloom, Shadows, Ambient Occlusion, Anti-Aliasing, Render Distance, LOD Distance, Sky Color, Exposure, Saturation, Contrast, Sharpness, Fog Density, HUD toggle | Visual settings restore correctly, restart requirements are clearly shown, performance effects are measurable |
| **0.7 — Gameplay & Physics** | Game Speed, Slow Motion improvements, Freeze Time, Frame Advance, Push Force, Acceleration, Max Speed, Friction Multiplier, Momentum Preservation, Landing Force Multiplier, Bail Threshold modifier, Instant Stop, Quick Respawn | Predictable behavior, safe value ranges, reliable reset-to-default behavior |
| **0.8 — Online Features** | Player List, Spectate Player, Teleport to Player where supported, Session Information, **Noclip when server-enabled**, **Forward Boost**, **Upward Boost**, server capability detection | Correctly detect server support, handle reconnects and respawns, clearly mark unavailable or server-controlled features |
| **0.9 — Overlays & Diagnostics** | **On-Screen FPS Overlay**, **Performance Diagnostics Overlay**, overlay positioning, size, opacity, scaling, toggle keybinds | Overlays remain lightweight, do not interfere with gameplay, scale correctly, and can be enabled independently |
| **0.9 — Trainer QoL** | Favorites, Search, Reset Setting, Reset Tab, Reset Everything, improved status indicators, configurable keybind interface | Fast navigation, reliable resets, settings remain readable as the trainer grows |
| **1.0 — Controller UI & Polish** | Native-style Controller Menu, full controller navigation, gameplay presets, camera presets, visual presets, physics presets, Import/Export config, compatibility checks, tooltips, documentation, changelog/version page, install/update/restore flow | Entire trainer usable without mouse/keyboard, stable configs, reliable updates, clean restore/uninstall |
| **Keybinds — Ongoing** | Controller + Keyboard bindings for every applicable feature, Hold/Toggle modes, controller deadzones, controller sensitivity options | No binding conflicts, keyboard and controller coexist properly, easy reset to defaults |

---

# Priority Features

- Controller Freecam
- On-Board FOV
- Off-Board FOV
- Off-Board Speed
- Off-Board Jump Height
- Footplant Speed
- Footplant Height
- Infinite Footplanting
- Allow Multiple Flips
- Gravity Multiplier
- Spin Speed
- Flip Speed
- Camera Follow Strength
- Camera Collision toggle
- Freeze Time
- Frame Advance
- Forward Boost
- Upward Boost
- Server-enabled Noclip
- UI Scale
- On-Screen FPS Overlay
- Performance Diagnostics Overlay
- Controller Menu

---

# 0.9 — Overlays & Diagnostics

## On-Screen FPS Overlay

A lightweight FPS overlay that can stay visible while skating.

Possible information:

- Current FPS
- Average FPS
- 1% Low FPS
- Frame time in milliseconds
- Compact mode
- Detailed mode
- Adjustable screen position
- Adjustable UI scale
- Adjustable opacity
- Toggle keybind

Example:

`FPS: 143 | Frametime: 6.9 ms`

The overlay should remain extremely lightweight and should not noticeably affect game performance.

---

## Performance Diagnostics Overlay

A more advanced overlay for figuring out why performance is dropping.

Possible information:

- Current FPS
- Average FPS
- 1% Low FPS
- Frame time
- Frame-time spikes
- CPU frame time
- GPU frame time, if accessible
- RAM usage
- VRAM usage
- Resolution
- Current graphics settings
- Render Distance
- LOD state
- Game Speed
- Session uptime

Example:

```text
Partvision's Reskate Trainer — Performance

FPS             138
Average         142
1% Low          106
Frame Time      7.2 ms

CPU Frame       4.1 ms
GPU Frame       6.8 ms

RAM             8.4 GB
VRAM            6.2 GB

Resolution      1920x1080
```

If Partvision's Reskate Trainer can determine it reliably, the overlay could also display:

- GPU Bound
- CPU Bound
- Unknown Bottleneck

The overlay should support:

- Compact mode
- Full mode
- Adjustable scale
- Adjustable position
- Adjustable opacity
- Toggle keybind

---

# Controller Menu

The Controller Menu allows the player to control Partvision's Reskate Trainer using a controller.

The Controller Menu should use an in-game style interface inspired by the native Reskate menus instead of requiring the ImGui menu.

## Opening the Controller Menu

**Hold D-Pad Left + press R3**

This combination should open or close the Controller Menu.

## Suggested Controls

- **D-Pad Up / Down** — Navigate options
- **D-Pad Left / Right** — Change values
- **A / Cross** — Select or toggle
- **B / Circle** — Back
- **LB / RB** — Switch tabs
- **X / Square** — Reset selected setting
- **LT / RT** — Fine or coarse value adjustment
- **Hold D-Pad Left + R3** — Open or close Partvision's Reskate Trainer

The Controller Menu should mirror Partvision's Reskate Trainer menu structure:

- Home
- Player
- Lobby
- Visual
- Performance
- Info

This prevents Partvision's Reskate Trainer from needing two completely different menu systems internally.

---

# Online Feature Behavior

Online-specific features should clearly display whether they are supported by the current server.

Possible states:

**Available** — Supported by the current server.

**Unavailable** — The server does not expose or allow the feature.

**Unknown** — Partvision's Reskate Trainer cannot currently determine support.

This especially applies to:

- Noclip
- Forward Boost
- Upward Boost
- Teleport to Player
- Future host/session controls

Partvision's Reskate Trainer should not present server-dependent features as guaranteed functionality.

If a feature is unavailable, its control should be disabled and the trainer should explain why.

---

# Online Features

## Noclip

Noclip should only be available when the current server supports or activates it.

More information can be based on behavior already found in existing Reskate trainer implementations.

The trainer should clearly display whether Noclip is currently:

- Available
- Unavailable
- Unknown

---

## Forward Boost

Applies a boost in the player's forward direction.

Possible options:

- Boost strength
- Hold or press mode
- Controller keybind
- Keyboard keybind
- Cooldown if required
- Server support indicator

---

## Upward Boost

Applies an upward boost to the player.

Possible options:

- Boost strength
- Hold or press mode
- Controller keybind
- Keyboard keybind
- Cooldown if required
- Server support indicator

---

# Trainer UI Structure

Partvision's Reskate Trainer should continue using the current six main tabs:

## Home
- Trainer status
- Version information
- Quick actions
- Active override count
- Reset all active overrides
- Update/change information

## Player
- Tricks
- Movement
- Physics
- Off-board controls
- Gravity
- Spin
- Flip
- Footplant settings
- Boost settings

## Lobby
- Player List
- Spectate Player
- Teleport to Player
- Session Information
- Noclip
- Forward Boost
- Upward Boost
- Server support status

## Visual
- Freecam
- Controller Freecam
- FOV
- Camera settings
- Post-processing
- HUD
- Visual overrides

## Performance
- Render Distance
- LOD
- Anti-Aliasing
- Shadow settings
- Performance overrides
- FPS Overlay
- Performance Diagnostics Overlay

## Info
- Trainer version
- Reskate client build
- Reskate client compatibility
- Movement telemetry
- Position
- Velocity
- Jump information
- Debug information
- Credits
- Settings path

---

# Misc Features

## UI Scale

Allow Partvision's Reskate Trainer ImGui interface and overlays to be resized.

Possible presets:

- 75%
- 90%
- 100%
- 110%
- 125%
- 150%
- Custom

The value should persist between launches.

---

## Modified Value Indicators

Any setting that differs from its normal/default value should be visibly marked.

Possible examples:

`Gravity Multiplier: 0.75x *`

or

`MODIFIED`

The user should be able to reset individual modified values without resetting the entire trainer.

---

## Reset Controls

Partvision's Reskate Trainer should support:

- Reset selected setting
- Reset current tab
- Reset all active overrides

Resetting should always restore the original Reskate client value whenever possible.

---

# Presets

Planned preset categories:

## Gameplay Presets
Groups of player/gameplay settings.

## Camera Presets
Saved FOV and camera configurations.

## Visual Presets
Saved visual and post-processing configurations.

## Physics Presets
Saved gravity, friction, speed, spin, flip, and movement settings.

Presets should support:

- Save
- Load
- Rename
- Delete
- Import
- Export

---

# Keybinds

Controller and keyboard bindings should be supported for every applicable trainer feature.

Keybind features:

- Keyboard bindings
- Controller bindings
- Multiple binds where useful
- Hold mode
- Toggle mode
- Controller deadzones
- Controller sensitivity
- Reset binding
- Conflict detection

Keyboard and controller bindings should be able to coexist without interfering with one another.

---

# Partvision's Reskate Trainer UI Systems

Partvision's Reskate Trainer will effectively have three different UI systems:

## ImGui Trainer
Main development and mouse/keyboard interface.

## Controller Menu
Native-style controller interface for controlling Partvision's Reskate Trainer without a mouse.

## Gameplay Overlays
Information displayed directly over gameplay.

These overlays include:

- FPS Overlay
- Performance Diagnostics Overlay

Keeping these systems separate allows each one to be designed specifically for its intended use.


## 0.4 development status - preview 4

Player is grouped into Tricks, Movement, Off-board and Physics. Native off-board desired speed, local movement gravity and horizontal air steering are implemented as experimental solo controls with values, bindings and individual reset. No Fall adds 26 landing/collision tuning overrides to native bail filtering. Off-board jump height now uses a native ground-to-falling edge rather than wall-clock movement detection.

The release gate remains open: animation/trajectory off-board jumps and repeated board kickflips still need implementation, infinite footplant chaining needs verification, and new native behavior needs in-game collision/landing/respawn testing. The body-flip constraint's supported default is already off. Build/config/field reset/UI and movement-math checks pass; they do not replace a game test. Full controller feature bindings/menu navigation remain later work.
