# Particle Wet Splatter Template Reference

This component is a template for splatters created by the [Particle Wet Splatter](../ParticleWetSplatter) component. When the particle wet splatter component needs to create a new splatter it will pick a random template and copy the settings from the template to the new splatter.

All settings not listed here are _exactly_ the same as the [Wet Decal Component](../WetDecal).

## Probability

This is the chance of this template being selected when a new splatter is created. It is normalized to the sum of all probabilities of all templates on the same component.

For example if there are 3 templates with probabilities of `1`, `0.5` and `0` the sum is `1.5` and the chance of each template being selected it `66%`, `33%` and `0%`.