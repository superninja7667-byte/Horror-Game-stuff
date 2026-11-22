# THE FOREST — PC-first game and Android test APK

The main game is being developed for PC / PCVR. The Android project exists only as a separate device-test wrapper. **An APK cannot be installed on an iPad**; use the HTML build in iPad Safari for browser testing. A native iPad app requires a separate iOS/Xcode build on macOS.

## Preserve existing GitHub assets

Keep these existing root files in this repository:
- `tree-low-poly-lowpoly.zip`
- `campfire.glb`
- `rock.zip`

## Add the repair build files

Download and extract `THE_FOREST_GitHub_Repair_Upload_Pack.zip`, then merge its contents into this repository root without deleting existing files. Upload the files at their included paths. Important new files are:

- `app/src/main/assets/index.html` — repaired game HTML entrypoint
- `rootbound_sentinel.fbx` — monster model
- `player-assets-pack.zip.part00`
- `player-assets-pack.zip.part01`
- `player-assets-pack.zip.part02` — upload all three unchanged

Each player chunk is below GitHub's per-file browser-upload size limit. Do not unzip or rename them. The workflow joins the chunks, verifies the ZIP, extracts the player FBX and texture maps, copies the existing tree/campfire/rock assets into the APK, verifies all required inputs, then compiles `:app:assembleDebug`.

## Build the APK

Push the merged files to `main`, or open **Actions → Build THE FOREST APK → Run workflow**. The workflow now fails early with a missing-file message when an input asset is absent. A successful run means Gradle compiled the APK and the artifact upload step ran.

Download the `THE-FOREST-Android-APK` artifact ZIP from the successful run, extract it, then install `app-debug.apk` on an Android device.

Three.js and the FBX/GLTF/ZIP loaders are loaded from jsDelivr, so the current build requires an internet connection. The APK is an Android test build, not an iPad or iOS package.
