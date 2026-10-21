# SALARX Open City 3D

An original browser-based 3D open-city driving and exploration prototype built with Three.js. It takes broad inspiration from classic open-world city games, while using original procedural content rather than GTA code, maps, characters, missions, models, textures, or music.

## Play online

If GitHub Pages is enabled for this repository (Settings → Pages → Deploy from a branch → `main` → `/(root)`), play at:

**https://salarkhurram989.github.io/gta/**

The browser version loads Three.js from jsDelivr, so an internet connection is required.

## Current prototype features

- Procedural 3D city blocks, buildings, roads, trees and street markings
- Third-person player movement and sprinting
- Sports coupe with steering, acceleration, reverse and braking
- 64 procedurally generated pedestrians with short individual conversations
- Ambient moving traffic and broken road markings around intersections
- Four interactable shops: in-game weapon shop, cafe, clothing store and auto shop
- Spend earned cash on fictional game weapons, meals, outfits and car paint
- Target-practice interaction for purchased weapons (non-graphic; targets only)
- Courier destinations, cash rewards and delivery counter
- Minimap, speed HUD and mobile touch controls
- Keyboard pause/resume with **P**
- Local progress saving after completed deliveries

## Controls

- **WASD / Arrow keys** — move or drive
- **Shift** — sprint while on foot
- **E** — enter or exit the sports car (stand close to it)
- **Space** — brake while driving
- **F** — talk to nearby pedestrians or open a nearby shop
- **G** — use purchased equipment at the practice targets
- **Esc** — close dialogue/shop panels
- **P** — pause/resume
- On phones/tablets, use the on-screen controls and **TALK** button

## Android APK

The Android WebView wrapper and GitHub Actions workflow are in `android/` and `.github/workflows/build-android-apk.yml`.

- Build workflow: https://github.com/salarkhurram989/gta/actions/workflows/build-android-apk.yml
- Releases: https://github.com/salarkhurram989/gta/releases
- APK builds are debug builds. Only install an APK from a release after checking that the corresponding workflow succeeded.
- The Android build currently loads the Three.js engine from the network, so it requires internet access.
- Android 4.0.4 compatibility on Samsung Galaxy Tab 10.1 SHW-M380K is **not verified on physical hardware**. A successful APK build does not prove that the tablet's WebView supports the required WebGL features or can run the game smoothly.

## Development documents

- [Engineering master prompt](docs/MASTER_PROMPT.md)
- [Staged development roadmap](docs/DEVELOPMENT_ROADMAP.md)
- [QA and acceptance checklist](docs/TEST_PLAN.md)

## Known limitations

This is an evolving prototype, not a full commercial-scale open-world game. Pedestrian and traffic behavior is lightweight and not yet equivalent to robust pathfinding or a complete traffic simulation. The mission loop currently focuses on courier deliveries. Shops, basic NPC conversations and target practice are prototype systems; the ten-mission framework, vehicle garage, advanced police AI, audio and weather are future stages. Gameplay and physical-device compatibility still need testing. Features should be considered verified only after the tests in the QA checklist have actually been run.
