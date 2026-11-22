# THE FOREST — PC-first game and Android test APK

The HTML/WebGL build is the primary PC development build. The Android wrapper is only an additional test target; it does not change the primary PC control layout or game design.

## Upload the updated game HTML

1. Download `THE_FOREST_Asset_Texture_Inventory_Fix.html` from the ChatGPT update.
2. Open `app/src/main/assets/` in this repository.
3. Upload the HTML there and name it exactly `index.html`.

## Upload the player model pack

Upload all three split files to the repository root (do not unzip them in GitHub):

- `player-assets-pack.zip.part00`
- `player-assets-pack.zip.part01`
- `player-assets-pack.zip.part02`

The workflow joins those parts, tests the ZIP, and extracts `player-assets/model/player.fbx` plus the full player texture set into the Android app assets.

The environment assets are already in the repository root and are copied into the APK automatically:

- `tree-low-poly-lowpoly.zip` — supplied Tree 1 and 2 FBX and Tree.png
- `campfire.glb` — new campfire model
- `rock.zip` — new rock model pack and textures
- `rootbound_sentinel.fbx` — Rootbound Sentinel monster model

The Rootbound Sentinel FBX must also be uploaded to the repository root as `rootbound_sentinel.fbx`; it is included in the APK.

## Build and download

After the HTML, all three player parts, and `rootbound_sentinel.fbx` have been uploaded, the **Build THE FOREST APK** GitHub Actions workflow runs automatically. The workflow now fails explicitly when a required file is missing, validates the ZIP assets, compiles the Android app, checks the APK exists, and publishes it as the `THE-FOREST-Android-APK` artifact.

Open the repository's **Actions** tab, open the successful run, and download the artifact. Extract it and install `app-debug.apk` on a supported Android device.

The APK build uses Java 17, Android SDK 36, Android Gradle Plugin 9.4.0, and Gradle 9.6.0. The project pins these compatible toolchain versions. Three.js and its model loaders are currently imported from jsDelivr, so a network connection is required when launching the game.

## iPad note

An Android APK cannot be installed on an iPad. For iPad testing, use the HTML build in Safari (or as a home-screen web app), or create a separate signed iOS `.ipa` build through Xcode/TestFlight.
