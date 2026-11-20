# THE FOREST Android APK

This project wraps the browser game in a fullscreen Android WebView. It enables JavaScript, hardware acceleration, local asset loading, audio playback, and the optional player-microphone permission used by the in-game test panel.

## Add the game source

1. Download `THE_FOREST_Truck_Radio_Intro.html` from the ChatGPT build output.
2. Copy it to `app/src/main/assets/index.html` (the filename must be exactly `index.html`).
3. Commit and push the file to the repository's `main` branch.

The workflow checks for both `app/src/main/assets/index.html` and the repository-root `rootbound_sentinel.fbx`. It skips the Gradle build until both are present rather than producing an empty app.

## Build with GitHub Actions

Open the repository's **Actions** tab and run **Build THE FOREST APK**, or push a commit that changes the Android project/game HTML. Once `index.html` is present, the workflow builds a debug APK and uploads it as the `THE-FOREST-Android-APK` artifact. Download that artifact ZIP, extract it, and install `app-debug.apk` on the Android device.

The debug APK is for testing and does not require release signing. The workflow also copies the repository's `tree-low-poly-lowpoly.zip` into the app assets so the imported Tree 1 and 2 FBX and Tree.png texture load locally. Three.js is currently loaded from jsDelivr, so the device needs an internet connection when opening the game. The radio dialogue is bundled in the HTML and does not require a separate audio file.
