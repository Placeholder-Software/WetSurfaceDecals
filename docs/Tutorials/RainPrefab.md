### Rain

This prefab builds upon the puddle effect, by also including a rain drop effect. As the animation progresses, rain drops land randomly around the surface. Eventually, the entire surface becomes damp, and puddles begin to form. Towards the end of the animation, the damp areas begin to dry, and the puddles slowly shrink.

[gif of rain]

The effect is achieved by adding a white noise channel to the layer texture. To begin, the white noise layer is threshold against a very small threshold window, such that values quickly proceed from below the threshold region (0 output) to above (1 output) causing dots to appear randomly as the threshold region is swept downwards during the animation. The output range of this channel is also adjusted such that the maximum saturation output is ~0.5 (damp) rather than 1 (puddle).

[picture of dots of rain]

Later in the animation, the perlin noise channel is brought in, in the same manor as with the Puddles prefab, in order to form puddles. There are two such channels in this effect, with the second used later for drying.

[picture of fully damp area with puddles]

The animation finishes by drying the area. The 2nd perlin noise channel has its threshold range broadened (increased softness), and the range is gradually raised. This causes regions furter away from the puddles to lighten as they dry. At the same time, the first perlin noice channel has its threshold gradually raised, which causes the puddles to shrink.

[picture of drying puddle]