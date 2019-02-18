# Base External Wetness Source Reference

This is the base class for "wetness source" components. To integrate Wet Stuff with a new weather system you should extend this class and implement the one property to extract data from the weather system.

## `float RainIntensity { get; }`

This property should fetch the current intensity of the rain. The result should be between 0 (not raining) to 1 (torrential downpour).