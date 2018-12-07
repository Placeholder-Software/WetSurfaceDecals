Wet Stuff has several component which make it east to integrate puddle with any dynamic weather system. It's easy to extend these components to support any weather system.

We have already integrated Wet Stuff with Enviro, check out the asset store to download it for free (requires Enviro and Wet Stuff).

## Wetness Source

This [Wetness Source](/Reference/BaseExternalWetnessSource) component reads data from the weather system for Wet Stuff. There will be a different version of this component for each weather integration, if you want to integrate with a custom weather system you should implement this component.

For the Enviro integration this component is located in `Assets/PlaceholderSoftware/WetStuff/EnviroIntegration/EnviroWetness.cs`.

## Drip Line

![Drip Line](../images/EnviroDripHighlight.jpg)

The [Drip Line](/Reference/DripLine) component is located in `Assets/Plugins/PlaceholderSoftware/WetStuff/Weather/DripLine.cs`. This component automatically configures a particle emitter to slowly drip water from a line and automatically sets up [wet particle splatters](/GettingStarted/WetParticleSplatter) where the particles hit the floor. The rate of dripping is automatically controlled by the weather integration.

## Auto Rain Puddle

![Dry To Wet](../images/DryToWet.png)

![Dry To Wet](../images/WetToDry.jpeg)

The [Auto Rain Puddle](/Reference/AutoRainPuddle) component is located in `Assets/Plugins/PlaceholderSoftware/WetStuff/Weather/AutoRainPuddle.cs`. This component automatically animates wet decals to act like puddles in response to the weather integration.