# SALARX Open City 3D — Development Roadmap

This roadmap is intentionally staged. The repository currently contains a browser-based Three.js prototype with a player, one drivable car, a procedural city, courier markers, pedestrians, traffic, a minimap and a simple HUD. These systems are prototype-level; the presence of code is not proof of runtime correctness.

## Phase 0 — Baseline and build health
**Goal:** know what currently works before expanding it.

- Inspect the latest `index.html`, Android wrapper and CI workflow.
- Run JavaScript syntax checks and inspect console errors in a compatible browser.
- Verify Android preparation/transpilation and APK build.
- Record current commit, CI status, artifact URL, known issues and baseline performance.

**Exit criteria:** baseline report exists; no test result is inferred or fabricated.

## Phase 1 — Playable core loop (highest priority)
- Fix movement, camera, driving, entry/exit and collision edge cases.
- Align collision footprints with building geometry.
- Prevent mission rewards from being duplicated.
- Add pause/resume and restart.
- Add validated, versioned local save/load for cash, mission progress and settings.
- Make touch controls resilient to pointer cancellation and focus loss.

**Exit criteria:** start → explore → drive → complete one mission → receive one reward → save → reload works end-to-end.

## Phase 2 — Connected city and navigation
- Use deterministic road/building generation.
- Define road lanes and sidewalk waypoints.
- Add named original districts and a few readable landmarks.
- Synchronize minimap coordinates, mission markers and world scale.
- Check collision/navigation boundaries at all mission destinations.

**Exit criteria:** the player can reach every current destination without crossing building interiors; minimap markers match world positions.

## Phase 3 — Living city AI
- Replace arbitrary pedestrian movement with sidewalk waypoints and simple states.
- Add route-aware traffic, intersection behavior, spacing and obstacle avoidance.
- Add simple pedestrian reactions and traffic sounds only if affordable.
- Add population density settings and entity pooling.

**Exit criteria:** 5-minute sample test has no obvious building traversal, stuck entities, runaway spawning or visible teleporting near the player.

## Phase 4 — Vehicle variety and handling
- Add compact, sedan, sports, van and utility classes.
- Tune per-class acceleration, steering, braking, grip and dimensions.
- Add safe vehicle recovery, damage state and garage/vehicle selection.
- Keep collision behavior stable and frame-rate independent.

**Exit criteria:** all vehicle classes can start, turn, reverse, brake and exit without breaking the world state.

## Phase 5 — Data-driven mission engine
- Define mission states and data structures.
- Support prerequisites, briefings, objectives, checkpoints, timers, success/failure, retry and rewards.
- Convert existing courier loop to the framework.
- Add the 10 original mission types specified in the master prompt.
- Persist mission completion and unlocks.

**Exit criteria:** each mission is completable and retryable, with exactly-once rewards and reliable reload behavior.

## Phase 6 — Progression and optional systems
- Garage, vehicle selection and lightweight customisation.
- Collectibles, safehouse and optional activities.
- Day/night, street lighting, weather and original ambience where performance permits.
- Modular wanted/police pursuit system only after navigation and vehicle AI are stable.

**Exit criteria:** optional systems are independently testable and do not break the core loop.

## Phase 7 — UX and performance
- Title, pause, settings, controls, mission briefing/result and map/waypoint UI.
- Test touch targets and layouts at narrow mobile sizes and desktop.
- Add Low/Medium quality settings, reduced shadows and lower NPC counts.
- Handle WebGL unavailable, external dependency failure and invalid save data.

**Exit criteria:** no overlapping core controls; low-quality mode runs with reduced load; failures are explained to the player.

## Phase 8 — Release and compatibility
- Run syntax and gameplay smoke tests.
- Verify GitHub Actions build, APK artifact and release asset.
- Record actual APK size and whether it depends on network-loaded Three.js.
- Test on a modern desktop browser and Android device if available.
- Test Android 4.0.4 only on the actual target hardware before claiming support.

**Exit criteria:** release notes list exact commit, tested platforms, unverified assumptions, known limitations and a verified APK link if available.

## Test matrix

| Area | Minimum test | Pass condition |
|---|---|---|
| Startup | Load page and press Play | No uncaught error; HUD appears |
| Walking | Move in four directions and sprint | Responsive, bounded, collision-aware |
| Driving | Enter, accelerate, turn, reverse, brake, exit | No stuck mode or unsafe exit |
| Mission | Reach marker, remain in trigger | Exactly one reward per mission |
| Save | Complete mission, reload | Cash/progress restored and validated |
| NPCs | Observe routes for five minutes | No building traversal or permanent stalls |
| Traffic | Observe intersections/near-player behavior | Routes remain on roads; no uncontrolled collisions |
| Minimap | Compare player and marker to world | Coordinates and orientation are consistent |
| Mobile | Test portrait and landscape touch targets | Buttons remain visible and release cleanly |
| Android build | Run CI and inspect artifact | Build succeeds and APK asset exists |
| Legacy tablet | Install and launch on SHW-M380K | Claim support only if physically tested |

## Current risks to address early

- A Three.js prototype can contain APIs unsupported by older WebViews even if the APK's minimum SDK is low.
- A build success proves packaging, not gameplay correctness or tablet compatibility.
- NPC and traffic visuals are not equivalent to robust pathfinding.
- External engine delivery requires internet unless the engine is bundled locally.
- A full commercial-scale open world is much larger than a single HTML file; use staged improvements and measurable tests.
