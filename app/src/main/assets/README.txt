THE FOREST Android game assets

index.html
  The game entry point. Use THE_FOREST_Inventory_Menu_Update.html from this update and name it index.html.

player-assets/
  Upload the three files named player-assets-pack.zip.part00, .part01, and .part02 to the repository root. The workflow joins them and extracts player-assets/model/player.fbx and its texture maps into this folder.

campfire.glb and rock.zip
  Supplied by the repository owner. The Android workflow copies them from the repository root into app assets before building.

tree-low-poly-lowpoly.zip
  The supplied Tree 1 and 2 FBX plus Tree.png. The workflow copies this from the repository root.

rootbound_sentinel.fbx
  Optional Rootbound Sentinel model. If present, the Android workflow copies it into app assets. A missing monster FBX no longer prevents a test APK from building.

Three.js and the FBX/GLTF/JSZip loaders are imported from jsDelivr, so the game engine requires an internet connection. The game is not fully offline at this stage.
