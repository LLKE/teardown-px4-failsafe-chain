## Hidden Invariant

> **🚨**
> All failsafe actions must fit a single global priority and fallback ordering, where “higher” actions are always safer/more appropriate than “lower” ones across every trigger context. 

### Why this invariant exists

To allow for a safe handling of system failures, a failsafe action must always be selected in case of a system failure, even if the original failsafe cannot run. The invariant ensures that a chain of possible actions exists, that can be selected in ascending order in case the best action cannot run.

### What assumes it

The function that is responsible for checking if the selected action can run is constructed as a switch-case statement which falls through the selected actions until one is found that can run. 

### What modifies it

A new failsafe action that is added, e.g. to handle an edge case such as data link loss at low altitude.

### Why it is currently implicit

The chain only works correctly if every newly added action is placed so that this implicit ordering still preserves cause-specific intent (for example, battery-critical intent must not be accidentally outranked and rewritten by unrelated actions).

There is no explicit check that ensures that failsafe actions are safe for certain system failures, which can lead to dangerous behaviour during a system failure.
