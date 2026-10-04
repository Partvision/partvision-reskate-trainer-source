# Partvision's ReSkate Trainer

Custom ReSkate 1.0.6 build for Skate Steam build 25414733. Current preview: **0.4.0-preview1**.

## Downloads

- [Installer package — 0.4 preview](Partvision-ReSkate-Trainer-0.4-preview1.zip)
- [Complete corresponding source](Partvision-ReSkate-Trainer-source.zip)
- [Installation, controls and limitations](INSTALL.md)
- [Windows build instructions](BUILD-PARTVISION.md)

The source archive contains the complete modified ReSkate project, trainer code, build files, dependency sources, license notices and roadmap. Extract it before building. The source is currently stored as an archive in this repository.

## Current features

New 0.4: experimental footplant launch tuning, pop preservation, body flips/spins, a one-shot slingshot, independent resets and UI scaling.

Home-key ImGui menu with six tabs; ollie power, slow motion, speed boost, noclip/fly, experimental off-board jump assistance, keybinds and presets; freecam, freecam FOV 40–120, film grain, vignette and chromatic aberration; FPS comparison, shadow maps and five category-specific cull distances.

Player overrides are solo-only. Local rendering controls are intended to work in multiplayer, but server behavior has not been playtested. This preview passed build and automated UI checks; in-game validation remains pending.

## New roadmap

[ROADMAP.md](ROADMAP.md) defines the updated 0.4–1.0 plan. 0.4 is now in progress: the first Tricks & Movement controls, UI scaling and per-feature resets are in the preview. Off-Board Speed, general Gravity Multiplier, Air Control, broader reset/indicator coverage and in-game validation remain pending. Controller cameras, visuals, physics, server capabilities, gameplay overlays and controller UI follow in later milestones. Planned features are not yet implemented.

## Credits and license

Created for Partvision with OpenAI Codex. Based on ReSkate by Dingo-Shenanigans, v1.0.6 / commit `f815658bf1833ef0580fc87ea1758bfd91ddb361`. Physics and off-board helper adaptations come from Andrew Nakas's ReSkate Trainer. Uses Dear ImGui and bundled dependencies under their respective licenses.

GPL-3.0; see [LICENSE](LICENSE). Full dependency notices and upstream documentation are in the source archive. This is an unofficial fan project, not affiliated with Electronic Arts or Full Circle. You need your own copy of Skate.
