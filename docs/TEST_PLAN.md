# SALARX Open City 3D — QA Checklist

## Build / static checks
- [ ] JavaScript syntax check passes.
- [ ] Android preparation script completes.
- [ ] APK build workflow completes successfully.
- [ ] APK artifact is present and downloadable.
- [ ] Release asset corresponds to the latest tested commit.
- [ ] Browser console has no uncaught startup errors.

## Gameplay smoke test
- [ ] Title screen loads and Play starts the game.
- [ ] WASD/arrows move the player and Shift sprints.
- [ ] E enters the vehicle only when close enough.
- [ ] Driving supports forward, reverse, steering and brake.
- [ ] E exits at a clear location and never inside a building.
- [ ] Player and car collide with building boundaries.
- [ ] Mission marker is reachable and updates after completion.
- [ ] Staying in a completed marker does not grant repeat rewards.
- [ ] Cash and mission progress persist after reload.
- [ ] Invalid save data falls back safely.
- [ ] Pause/resume/restart works if implemented.

## City simulation
- [ ] Pedestrians spawn on sidewalks.
- [ ] Pedestrians avoid buildings and recover from blocked routes.
- [ ] Traffic follows roads and stays outside buildings.
- [ ] Traffic doesn't visibly teleport beside the player.
- [ ] No unbounded object creation occurs in the animation loop.
- [ ] Low quality reduces expensive effects/population.

## Platform verification
- [ ] Modern desktop browser test recorded with browser/version.
- [ ] Mobile browser test recorded with device/browser.
- [ ] Android APK installs and launches on a real device.
- [ ] Android 4.0.4 compatibility is marked unverified unless tested on the target tablet.
- [ ] Network requirement for Three.js is documented.

Record results as **Pass**, **Fail**, or **Not run**. Never convert Not run into Pass.
