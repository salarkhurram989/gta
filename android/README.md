# Open City 3D Android APK

This project wraps the browser game in a fullscreen Android WebView and builds a debug APK through GitHub Actions.

## Build
Push changes to `main` or manually run **Actions → Build Open City 3D APK → Run workflow**. Download the APK from the workflow run's **Artifacts** section. The workflow also attempts to publish a GitHub release APK.

## Compatibility
- Manifest minimum SDK: Android 4.0.3 (API 15).
- Build script transpiles game JavaScript to ES5 and switches the APK copy to Three.js r110 for older WebViews.
- Internet is required to download Three.js.
- Android 4.0.4 / Tegra 2 WebGL support and frame rate are not verified on physical hardware. A minimum SDK value does not guarantee smooth gameplay.
- Debug APK, not production-signed.
