# SALARX Open City 3D

An original browser-based 3D open-city driving and exploration prototype built with Three.js. It takes broad inspiration from classic open-world city games, while using original procedural content rather than GTA code, maps, characters, missions, models, textures, or music.

## Play online

If GitHub Pages is enabled for this repository (Settings → Pages → Deploy from a branch → `main` → `/(root)`), play at:

**https://salarkhurram989.github.io/gta/**

The browser version loads Three.js from jsDelivr, so an internet connection is required.

## Current prototype features

- Procedural 3D city blocks with enhanced facade details, rooftop equipment, ACES tone mapping, updated lighting, depth fog and a gradual day-night cycle
- Glowing hidden city caches worth $75 each, marked on the minimap and saved when collected
- Select buildings have doors and walkable furnished interiors; shop interiors are enterable too
- Roads, sidewalks, trees and street markings
- Third-person player movement and sprinting
- Sports coupe with steering, acceleration, reverse and braking
- 64 procedurally generated pedestrians with short individual conversations
- Ambient moving traffic and broken road markings around intersections
- Four interactable shops: arcade, cafe, clothing store and auto shop
- Spend earned cash on arcade tokens, meals, outfits and car paint
- Courier destinations, cash rewards and delivery counter
- Minimap, speed HUD and mobile touch controls
- Keyboard pause/resume with **P**
- Manual **SAVE GAME** button plus automatic saves every 15 seconds and when leaving the page
- Save/load restores cash, deliveries, mission progress, shop inventory, collected caches, player position and vehicle position
- Existing version-1 local saves are migrated by loading them into the expanded save format

## Controls

- **WASD / Arrow keys** — move or drive
- **Shift** — sprint while on foot
- **E** — enter/exit the sports car, or exit a building
- **F** — enter a building/shop door; inside a shop, open its purchase menu
- **Space** — brake while driving
- **F** — talk to nearby pedestrians or open a nearby shop
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

This is an evolving prototype, not a full commercial-scale open-world game. Pedestrian and traffic behavior is lightweight and not yet equivalent to robust pathfinding or a complete traffic simulation. The mission loop currently focuses on courier deliveries. Building interiors, shops, basic NPC conversations and arcade-token purchases are prototype systems; the ten-mission framework, vehicle garage, advanced police AI, audio and weather are future stages. Gameplay and physical-device compatibility still need testing. Features should be considered verified only after the tests in the QA checklist have actually been run.
