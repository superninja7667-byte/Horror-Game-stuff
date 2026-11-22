# THE FOREST Android APK

This project wraps the game in a fullscreen Android WebView with JavaScript, hardware acceleration, bundled local assets, audio playback, and the optional microphone permission used by the in-game mic test panel.

## Add the latest game HTML

1. Download `THE_FOREST_Inventory_Menu_Update.html`.
2. Upload it to `app/src/main/assets/index.html` (the filename must be exactly `index.html`).

## Add the player model

The player FBX and supplied textures are split into three files because each part is kept below GitHub's browser-upload file-size limit:

- `player-assets-pack.zip.part00`
- `player-assets-pack.zip.part01`
- `player-assets-pack.zip.part02`

Upload all three files to the repository root. The workflow joins and extracts them into `app/src/main/assets/player-assets/`.

The repository's `campfire.glb`, `rock.zip`, and tree ZIP are copied into app assets automatically. The Rootbound Sentinel FBX is optional for an APK build.

## Build with GitHub Actions

Open the repository's **Actions** tab and run **Build THE FOREST APK**, or push a commit that changes the Android project, game HTML, or listed assets. Once `app/src/main/assets/index.html` is present, the workflow builds a debug APK and uploads it as the `THE-FOREST-Android-APK` artifact.

Download the artifact ZIP, extract it, and install `app-debug.apk` on the Android device.

The APK is a debug test build and does not require release signing. Three.js and its FBX/GLTF/JSZip loaders are currently loaded from jsDelivr, so an internet connection is required when playing. This is not yet a fully offline release package.
