# 3. Short Lived Particle Splatters

> This demo is located at `"Assets/PlaceholderSoftware/WetSurfaceDecals/Demos/5. Particles (Drip Drip Drip)"`

![Demo Scene 4](../images/DemoScene5Particles.png)

This scene demonstrates a continuous dripping of particles with a sub-emitter burst of particles triggered when a particle collides with the floor. These two particle system use different configurations for the `Particle Wet Splatter`.

The main dripping particle system emits one single particle per second which falls under gravity and hits the floor, when it hits the floor it immediately dies. The `Particle Wet Splatter` component creates a decal at the point of impact, this is configured for a fairly small number (45) of particles which do not fade. Once a puddle has formed at the drip impact point it will stay there forever.

The sub-emitter burst also has a `Particle Wet Splatter` component, however this one is configured very differently. There is a lower chance that each impact will create a decal. Each decal will have a lifetime of 10-30 seconds, over this lifetime it will fade away (reducing saturation to zero). Recycling is enabled so dead decals will be re-used, creating an endless number of puddles for as long as the particle system keeps running.

### Adjustments

Try adjusting the following and observing how the scene changes:

 - Add a lifetime and enable recycling on the primary emitter. Notice how the puddle slowly fades away over the lifetime, but new particles keep being added maintaining a puddle on the floor.

 - Disable recycling on the sub-emitter. Notice how after 200 total particles have hit the floor no new puddles are ever created (because they cannot be recycled).

 - Lower the sub-emitter decal limit to 50. Notice how the number of decals being created is reduced as the number of decals which exist increases (controlled by the `Decal Count Limit > Decal Chance` curve).
    - Increase `Max Accelerated Ageing` to 3, this will accelerate the ageing of a random decal when there are insufficient decals. This can slightly help with low decal limits.
    - Increase `Steal Threshold` to 0.0025. This will "steal" a an active decal to create a new one if it is below the stealth threshold. The value for each decal is (Area * Saturation), since the decal are _approximately_ 0.1 x 0.1 (before randomized size) this will steal decals which are at 0.25 saturation and below. This will also help with low decal limits.