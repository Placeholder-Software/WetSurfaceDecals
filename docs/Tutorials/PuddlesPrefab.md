### Puddle Prefab

This prefab creates a puddle of water that grows as the animation progresses.

The effect is achieved by using a perlin noise texture to define saturation layers. This texture is then clipped against a threshold region which is shifted downwards as the animation proceeds. As the threshold falls, more of the noise texture is included in the output.

[gif? of puddles]