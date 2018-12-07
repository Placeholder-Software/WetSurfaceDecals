# Base External Wetness Source Reference

This is the base class for "wetness source" components. To integrate Wet Stuff with a new weather system you should extend this class and implement the two abstract properties.

## `float CurrentWetness { get; }`

This property should fetch the current level of "environmental wetness" from the weather system. The result should be between 0 (completely dry) to 1 (completely drenched).

## `float DeltaWetness { get; }`

This property should fetch the change per second in the level of environmental wetness from the weather system. This means that when it is raining the value should be positive and when it is not raining it should be zero (not getting drier) or negative (drying).