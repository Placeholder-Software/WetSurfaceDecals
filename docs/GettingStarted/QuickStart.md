## 1. Import Wet Decals

Import the Wet Decals asset into your project. Every time you import a new version of Wet Decals a window will pop up offering to take you to the latest changelog, you can launch this window again by navigating to Windows > Wet Decals > Welcome Screen.

## 2. Add `WetSurfaceDecals` script to your cameras

Add the `WetSurfaceDecals` script to each camera in your scene. Cameras must have this script attached for the decals to be visible from that camera.

> Ensure that the camera is rendering using the Deferred pipeline.

## 3. Place `WetDecalPuddle` prefab into your scene

Drag the `WetDecalPuddle` prefab located in `Assets/Placeholder Software/Wet Decals/Prefabs` into your scene view. This example prefab projects a puddle down onto any surface that lies within its bounds. See the [Wet Decal](/WetDecal.md) guide for more information on how to build your own decals.