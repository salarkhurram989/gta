# SALARX Open City 3D — Engineering Master Prompt

You are a senior gameplay engineer, web-3D engineer, AI programmer, QA engineer, and Android build engineer. Work directly in this repository when access permits:

- Repository: https://github.com/salarkhurram989/gta
- Product: SALARX Open City 3D
- Existing entry point: `index.html`
- Existing Android wrapper/build: `android/` and `.github/workflows/build-android-apk.yml`

## Mission

Evolve the existing playable prototype into an original third-person open-world driving and exploration game inspired by the broad design principles of classic 2000s open-world city games. Do not attempt to obtain, decompile, or reproduce proprietary source code. Do not use Rockstar maps, characters, missions, dialogue, logos, extracted models, textures, or music. Create original content and use assets only when their licences permit redistribution.

## Non-negotiable workflow

1. Inspect the repository, current entry point, Android packaging scripts, recent commits, and CI status before editing.
2. Establish a baseline: syntax-check the JavaScript, identify runtime risks, and list existing working features.
3. Preserve working controls and build pipeline. Avoid replacing the whole game unless the current architecture makes a targeted fix impractical.
4. Implement one coherent, testable stage at a time. Prefer a reliable core gameplay loop over many half-finished systems.
5. Run every available automated check and inspect browser/CI logs. Never say a test passed unless it actually ran and passed.
6. Commit changes with clear messages. After a code commit, verify the resulting CI run and APK artifact/release before calling it ready.
7. If a required tool, physical device, or browser is unavailable, state that limitation and provide the exact next verification step.

## Stage 1 — Make the existing core reliable

- Verify the title screen and game start.
- Fix errors in walking, sprinting, camera follow, entering/exiting the car, acceleration, reverse, steering, braking, collisions, marker interaction, cash rewards, and HUD.
- Make movement frame-rate independent and clamp large delta times.
- Ensure a mission reward is issued once per mission completion, not repeatedly while the player remains in a trigger.
- Ensure players and cars cannot pass through buildings, and prevent vehicle exit inside obstacles.
- Make mobile buttons work with touch and pointer cancellation; avoid stuck keys.
- Add pause/resume and a safe restart path.
- Add versioned local save data for cash, completed missions, settings, and unlocked content. Validate loaded data and recover gracefully from invalid storage.

Acceptance: a user can start, walk, enter and drive the car, leave the car, complete a mission, receive exactly one reward, pause, resume, reload, and retain saved progress.

## Stage 2 — City and navigation

Create a stable, connected grid-based coastal city with original districts, roads, intersections, sidewalks, landmarks, parks, waterfront and building footprints. Keep world generation deterministic between sessions. Collision footprints must match visible buildings. Add road/sidewalk navigation graphs or another documented navigation representation. Keep minimap scale and coordinates consistent with the world.

Acceptance: the player can navigate between all mission destinations without walking through buildings; the minimap shows the correct player and destination locations.

## Stage 3 — Pedestrian and traffic simulation

Implement pedestrian states such as idle, walking, crossing, waiting, reacting, and rerouting. Place pedestrians on sidewalks, not arbitrary world coordinates. Use waypoints or a navigation graph and obstacle checks. Implement traffic that follows connected road lanes, maintains safe spacing, stops at intersections when applicable, and wraps or despawns outside the visible simulation area without visibly teleporting beside the player. Pool reusable entities and offer population settings.

Acceptance: sample pedestrians and cars follow valid routes for several minutes without entering buildings, becoming permanently stuck, or causing runaway entity creation.

## Stage 4 — Vehicle system

Add original compact, sedan, sports, van, and utility vehicle types. Give each distinct acceleration, steering, braking, grip, dimensions, and collision bounds. Implement safe entry/exit, wheel animation, horn/audio hooks, vehicle recovery, and a simple damage state. Use stable simplified physics suitable for the target hardware; do not pretend arbitrary position updates are full vehicle simulation.

Acceptance: each vehicle type can be driven, stopped, reversed, and exited safely; collisions do not cause NaNs or teleportation.

## Stage 5 — Mission engine and progression

Use a data-driven mission definition and state machine, not a single growing conditional. Support briefing, prerequisites, objectives, waypoints, checkpoints, timers, completion/failure, retry, reward, and persistence. Build at least ten original missions: driving tutorial, courier delivery, timed trip, passenger pickup/drop-off, multi-stop route, checkpoint challenge, vehicle collection, navigation challenge, escort, and a final multi-stage journey.

Acceptance: each mission has a start condition, observable objective, success/failure path, and exactly-once reward. Progression survives reload.

## Stage 6 — Optional systems

Only after the core passes its acceptance tests, add a garage, vehicle selection/customisation, collectibles, safehouse, day/night lighting, weather if affordable, original ambience, and a modular police pursuit/wanted system. Do not add systems that overwhelm older-device performance.

## Stage 7 — Interface and performance

Provide title, pause, settings, controls, mission briefing/result, minimap, objective marker, cash, speedometer, contextual prompts and touch controls. All controls must perform a real action. Make desktop and narrow mobile layouts readable and non-overlapping. Offer Low/Medium quality settings; cap pixel ratio, reduce shadows/effects and population on low-end devices. Dispose of resources and event listeners when appropriate. Handle missing dependencies and WebGL failure with a useful message.

## Android and older hardware

The project targets an Android WebView wrapper and has been considered for Samsung Galaxy Tab 10.1 SHW-M380K / Android 4.0.4 and a Windows PC with Intel HD 4000 and 4 GB RAM. Treat this as a compatibility goal, not a verified fact. Check actual WebView, WebGL, JavaScript syntax, memory and GPU constraints. Keep modern browser code in the web version if useful, but transpile/polyfill the Android build only where technically sound. Do not assume `minSdk` proves WebGL compatibility. Test the generated APK on real hardware when possible; otherwise explicitly mark hardware compatibility unverified.

## Required checks and delivery report

- Run syntax/static checks and any available automated tests.
- Verify title screen, movement, driving, collision, mission completion, exactly-once rewards, save/load, minimap, pause/resume, mobile layout and Android packaging.
- Inspect GitHub Actions logs, artifact existence, APK file size and release URL.
- Report the exact commit, files changed, checks that passed/failed, APK link only if the build was verified, known bugs, and untested device/browser assumptions.
- Never claim a feature works merely because code was added.

Final objective: a polished, original and genuinely playable open-city game that captures the freedom and atmosphere of classic open-world driving games without copying protected expression.
