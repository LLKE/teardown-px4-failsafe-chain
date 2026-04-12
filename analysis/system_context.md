## System Context

The failsafe handling involves the following files:

**Framework**

`framework.h`
`framework.cpp`

This is where the failsafe chain is implemented, specifically in the function `getSelectedAction`.

Apart from that, for a failsafe action to be propagated all the way to an actual flight mode involves a mapping function called `modeFromAction`

**Failsafe**

`failsafe.h`
`failsafe.cpp`

In the function `checkStateAndMode`, using the macro `CHECK_FAILSAFE`, the module checks if a certain system failure has occurred and triggers a function call to functions `from<type of failure>Act`, which selects the action that should follow based on the type of failure.