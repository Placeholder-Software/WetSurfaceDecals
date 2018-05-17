The `WetParticleSplatter` script can be added to any game object that also contains a Shuriken particle system. Wet decals with be automatically placed wherever a particle collides with geometry. This can be used to create dynamic effects such as water pistols or leaking pipes.

> Collisions must be enabled on the particle system, and any geometry that you wish to be hit by particles must have a Collider.

## Example Setup

1. Add a `WetParticleSplatter` script to a Shuriken particle system. Ensure that "Collision" is enabled in the particle system configuration.
2. In the `WetParticlePlatter` configuration, enable "Lifetime" and set the "Min Lifetime" to 10 and "Max Lifetime" to 30. This will give decals spawned from collisions a random lifetime between 10 and 30 seconds. Decals will gradually fade off over the lifetime.
3. Enable "Randomize Size", and set "Min Inflation" to 0.5 and "Max Inflation" to 1.5. This will cause decals to vary in size as they spawn.
4. Enable "Randomize Orientation", and set "Random Degrees" to 180. This will cause decals to spawn with a random rotation applied.
5. Expand the "Wet Decal Settings" section, then expand "Horizontal Layers" and set the layer texture to the "Splatter" texture provided by Wet Stuff.

[screenshot of inspector showing configuration]

[gif of particle splatters]