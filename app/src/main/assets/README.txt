THE FOREST Android game assets

index.html
  The game entry point. Use THE_FOREST_Truck_Radio_Intro.html from the update.

rootbound_sentinel.fbx
  The Rootbound Sentinel model is copied here by the Android workflow from the repository root. For a local Gradle build, the app module Gradle task also copies it.

tree-low-poly-lowpoly.zip
  The supplied Tree 1 and 2 FBX plus Tree.png. The workflow copies this from the repository root. The standalone HTML fetches it from the public repository when the local file is not present.

Three.js is loaded from jsDelivr, so the game engine requires internet access. Radio dialogue and the other retained texture maps are bundled in index.html.
