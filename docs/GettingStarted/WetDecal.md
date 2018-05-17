The `WetDecal` script will project "wetness" onto any geomery surface that lies within its area. The geometry properties will be modified to simulate water saturation building up inside the microstructure of the surface, from slightly damp up to a thin film of water lying on top of the surface.

> Decals are only visible to cameras that have a `WetSurfaceDecals` script attached.

## Prefabs

There are prefabs included with Wet Stuff that provide example decals for common scenarios. It is recommended that you take a look at these before trying to define your own decals. These prefabs include both a pre-configured `WetDecal`, and a custom script which provides an animation slider to demonstrate how the fields on the decal can be adjusted to provide animation.

### Puddles

This prefab creates puddles of water that grow as their animation progresses. 

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

## Configuration

## Saturation

Saturation represents an overall "wetness" slider. Values from 0 to ~0.8 represent water building up within the surface, providing the effect of the surface getting progressively damper. Values from ~0.8 to 1 represent oversaturation - where a thin layer of water has built up over the surface to form a shallow puddle.

## Layers

Layers are textures which are projected either horizontally or vertically onto the surface and provide more detailed definition to the satutaion levels within the volume.

The value samples from the layer textures can be re-mapped from their [0,1] range to a different saturation range, and can be clipped against thresholds. Adjusting these ranges at runtime allows for animation of the decal.

Each of the four channels in a layer texture can controlled individually. The final saturation value is taken as the maximum of all channels.