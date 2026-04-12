## Failure Mode

 If a new failsafe action was added to the chain that is unsafe for certain system failures, this can lead to a crash in the worst case.

### Normal Behaviour

+ The actually selected action cannot run. 
+ The fallthrough chain falls through to the next, more severe action.
+ Falling back to a more severe action is safe and appropriate for all system failures

### Failure Behaviour

+ The actually selected action cannot run. 
+ The fallthrough chain falls through to the next, more severe action.
+ An action in the failsafe chain is not safe for one or more system failures.
+ This leads to risky or even dangerous behaviour if this is the action fallen back to.