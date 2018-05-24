The `WetDecal` script will project "wetness" onto any surface that it overlaps. The properties of the surface will be modified to simulate water saturation building up inside the microstructure of the surface, from slightly damp up to a thin film of water lying on top of the surface.

> Decals are only visible to cameras that have a `WetSurfaceDecals` script attached.

## A Simple Puddle

1. Create a new game object in your scene.
2. Attach a `Wet Decal` component.
3. Set `Saturation` to `1.0`, this will create a region of maximum wetness (a thin film of water covering the surface)
4. Move and scale the decal until it is the size and shape you want

This "puddle" doesn't look very good yet, it's just a square of wetness.

5. Change `Layer Mode` to `Single`, this will enable a single detail layer.
6. Expand the new detail layer and set the `Layer Mask` to `rgba-noise-freq-range`. This texture contains perlin noise, starting with high frequency noise in the Red channel down to low frequency noise in the alpha channel.
7. Change the green channel to `Simple Range Remap`. Tweak the `Threshold` and `Softness` values and observe how the puddle changes.

This is the most basic puddle you can create with Wet Stuff. Just a single channel of perlin noise, correctly thresholded to produce a good looking puddle.

## Demos / Prefabs

The demo scenes are contained in `Assets/PlaceholderSoftware/Demos`. Each scene demonstrates a single aspect of the asset and is built around a prefab which you can tweak and use in your own games.

It is recommended that you take a look through these prefabs and understand how they work to get a feel for the best way to achieve various effects.

### Puddle Prefab

This prefab creates a puddle of water that grows as the animation progresses.

The effect is achieved by using a perlin noise texture to define saturation layers. This texture is then clipped against a threshold region which is shifted downwards as the animation proceeds. As the threshold falls, more of the noise texture is included in the output.

[gif? of puddles]

### Rain

This prefab builds upon the puddle effect, by also including a rain drop effect. As the animation progresses, rain drops land randomly around the surface. Eventually, the entire surface becomes damp, and puddles begin to form. Towards the end of the animation, the damp areas begin to dry, and the puddles slowly shrink.

[gif of rain]

The effect is achieved by adding a white noise channel to the layer texture. To begin, the white noise layer is threshold against a very small threshold window, such that values quickly proceed from below the threshold region (0 output) to above (1 output) causing dots to appear randomly as the threshold region is swept downwards during the animation. The output range of this channel is also adjusted such that the maximum saturation output is ~0.5 (damp) rather than 1 (puddle).

[picture of dots of rain]

Later in the animation, the perlin noise channel is brought in, in the same manor as with the Puddles prefab, in order to form puddles. There are two such channels in this effect, with the second used later for drying.

[picture of fully damp area with puddles]

The animation finishes by drying the area. The 2nd perlin noise channel has its threshold range broadened (increased softness), and the range is gradually raised. This causes regions furter away from the puddles to lighten as they dry. At the same time, the first perlin noice channel has its threshold gradually raised, which causes the puddles to shrink.

[picture of drying puddle]

## Inspector Reference

The WetDecal component is a powerful component with a lot of configuration options exposed in the inspector. Make sure to read through the [Wet Decal reference](/Reference/WetDecal) which explains exactly what each part of the inspector does.