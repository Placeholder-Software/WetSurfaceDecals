The `WetDecal` script will project "wetness" onto any surface that it overlaps. The properties of the surface will be modified to simulate water saturation building up inside the microstructure of the surface, from slightly damp up to a thin film of water lying on top of the surface.

> Decals are only visible to cameras that have a `WetStuff` script attached.

## A Simple Puddle

1. Create a new game object in your scene.
2. Attach a `Wet Decal` component.
3. Set `Saturation` to `1.0`, this will create a region of maximum wetness (a thin film of water covering the surface)
4. Move and scale the decal until it is the size and shape you want

This "puddle" doesn't look very good yet, it's just a square of wetness.

5. Change `Layer Mode` to `Single`, this will enable a single detail layer.
6. Expand the new detail layer and set the `Layer Mask` to `rgba-freq-range`. This texture contains perlin noise, starting with high frequency noise in the Red channel down to low frequency noise in the alpha channel.
7. Change the green channel to `Simple Range Remap`. Tweak the `Threshold` and `Softness` values and observe how the puddle changes.

This is the most basic puddle you can create with Wet Stuff. Just a single channel of perlin noise, correctly thresholded to produce a good looking puddle.

## Demos / Prefabs

There are several demo scenes included in `Assets/PlaceholderSoftware/WetStuff/Demos`. Each scene demonstrates a single aspect of the asset and it is recommended that you take a look through these scenes and understand how they work to get a feel for the best way to achieve various effects.

## Inspector Reference

The WetDecal component is a powerful component with a lot of configuration options exposed in the inspector. Make sure to read through the [Wet Decal reference](../../Reference/WetDecal) which explains exactly what each part of the inspector does.