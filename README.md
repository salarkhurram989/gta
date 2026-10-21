# SALARX Open City 3D

An original browser-based 3D open-city driving and exploration prototype built with Three.js. Inspired by the *freedom and structure* of classic open-world city games, using original procedural content — not GTA code, maps, characters, missions, models, textures, or music.

## Play online

If GitHub Pages is enabled (Settings → Pages → Deploy from branch → `main` → `/(root)`):

**https://salarkhurram989.github.io/gta/**

Requires internet to load Three.js from jsDelivr.

## Implemented features (this revision)

- Procedural grid city with roads, sidewalks, buildings, shops, trees, day/night cycle
- Third-person on-foot movement (camera-relative) and sprinting
- **Three player vehicles** (Sports Coupe, City Sedan, Utility Van) with distinct acceleration, steering and top speed
- Garage near spawn — press **F** to cycle vehicles
- Enter/exit vehicles with obstacle-safe exit placement
- 64 pedestrians on sidewalk lanes + ambient traffic that occasionally turns at grid lines
- **Data-driven mission engine** with 10 original missions:
  1. Learn to Drive
  2. First Courier Run
  3. Cross-City Sprint (timed)
  4. Taxi Pickup (multi-point)
  5. Multi-Stop Route
  6. Checkpoint Challenge
  7. Vehicle Collection
  8. Minimap Navigator
  9. Local Escort
  10. City Circuit Finale
- Exactly-once rewards via claim flags (no duplicate payout spam)
- Mission briefing UI, success/fail, unlock progression
- **Wanted level** (★) from traffic collisions / hard impacts; cools down over time
- Four shops (arcade, cafe, clothing, auto) with interiors and purchases
- Hidden cash caches; minimap with player, mission, garage and caches
- Title screen with **New Game** / **Continue**; pause menu (P) with resume / restart / title
- Versioned local save (v2): cash, missions, inventory, caches, positions, vehicle, wanted
- Migrates v1 saves when present
- Customize panel: paint, outfit, camera distance, quality (Low/Med/High), ambience
- Mobile touch controls

## Controls

| Input | Action |
|--------|--------|
| WASD / Arrows | Move or drive |
| Shift | Sprint (on foot) |
| Space | Brake (driving) |
| E | Enter/exit vehicle or building |
| F | Talk, shop, garage cycle, accept mission near garage |
| P | Pause / resume |
| Esc | Close panels |

## Android APK

Wrapper and CI live under `android/` and `.github/workflows/build-android-apk.yml`.

- Builds: https://github.com/salarkhurram989/gta/actions/workflows/build-android-apk.yml  
- Releases: https://github.com/salarkhurram989/gta/releases  
- Debug APKs still load Three.js from the network (internet required).  
- **Android 4.0.4 / Galaxy Tab 10.1 SHW-M380K compatibility is not verified on physical hardware.**

## Known limitations

- Pedestrian/traffic AI is lightweight (no full pathfinding graph).
- Police are represented only as a wanted meter — no chase vehicles yet.
- No original audio engine / licensed soundtrack.
- Single HTML entry point; not a multi-scene commercial engine.
- Live browser and device testing of this revision is still required (syntax structure checked; runtime not executed in CI here).

## Development docs

- [Engineering master prompt](docs/MASTER_PROMPT.md)
- [Development roadmap](docs/DEVELOPMENT_ROADMAP.md)
- [Test plan](docs/TEST_PLAN.md)

## Build / run

1. Open `index.html` via any static server, or enable GitHub Pages.  
2. Or open the Pages URL above.  
3. Android: push to `main` triggers APK workflow when paths match.
