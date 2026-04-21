## Relevant Modules ([PX4-Autopilot v1.16.1](https://github.com/PX4/PX4-Autopilot/releases/tag/v1.16.1))

**Failsafe Framework**

PX4-Autopilot/src/modules/commander/failsafe/framework.hpp
PX4-Autopilot/src/modules/commander/failsafe/framework.cpp

Function of interest:
+ `getSelectedAction()` (implementation of failsafe fallback chain)
+ `modeFromAction()` (maps failsafe action to navigation state)

Failsafe Action Enum:
+ `enum class Action`

**Failsafe Checks**

PX4-Autopilot/src/modules/commander/failsafe/failsafe.hpp
PX4-Autopilot/src/modules/commander/failsafe/failsafe.cpp

Function of interest:
+ `checkStateAndMode()` (checks if system failures are active)