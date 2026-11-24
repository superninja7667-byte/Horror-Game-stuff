# THE FOREST — PC-first game and Android test APK

The main game targets PC / PCVR. The Android project is a separate test wrapper. APKs install on Android/Quest Android devices, not iPads; use Safari for iPad browser testing or prepare a separate native iOS build later.

## Current model/runtime assets already in this repository

- `three-runtime/` — local Three.js r160 addon modules, bridge and JSZip 3.10.1.
- `tree-low-poly-lowpoly.zip` — supplied Tree 1 and 2 FBX and Tree.png.
- `campfire.glb` — supplied animated campfire (the GLB contains a native animation clip).
- `rock.zip` — supplied nested OBJ model and rock color/normal/AO textures.

## Upload the latest game and character assets

Download and extract `THE_FOREST_GitHub_APK_Upload_Pack.zip`. Merge its contents into this repository without deleting existing assets:

- `app/src/main/assets/index.html` — latest Controls & Models game HTML
- `rootbound_sentinel.fbx` — Rootbound Sentinel monster model
- `player-assets-pack.zip.part00`
- `player-assets-pack.zip.part01`
- `player-assets-pack.zip.part02`

Each player chunk is below the GitHub web uploader's per-file limit. Upload all three unchanged to the repository root. The workflow joins and validates them, then extracts the FBX and textures under `app/src/main/assets/player-assets/`.

The Android workflow copies the local `three-runtime/` folder and existing tree/campfire/rock models into the APK. It validates all required game and model assets before invoking Gradle.

## Build the APK

Push the files above to `main`. GitHub Actions will run **Build THE FOREST APK**. A successful workflow run includes the `:app:assembleDebug` compile step and publishes a downloadable `THE-FOREST-Android-APK` artifact. Download that artifact ZIP, extract it, and install `app-debug.apk` on an Android device.

The APK is a debug test build, not a signed store release. The game models and Three.js addon modules are bundled locally; the standalone HTML still supports remote fallbacks when a PC build is served over localhost and network access is available.

## PC build

Use `THE_FOREST_PC_Controls_Models_Build.zip` for PC testing. Extract the entire folder and run `START_THE_FOREST.bat` (Python 3 required). This serves the game at localhost so ES module loaders and relative 3D assets work correctly.
