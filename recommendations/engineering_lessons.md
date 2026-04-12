## Engineering Lessons

1. Safety behavior should be policy-driven, not control-flow-driven.
If system-critical decisions are encoded implicitly in branches and ordering, behavior becomes fragile under change.

2. Decision logic should have one authoritative source of truth.
When policy is split across multiple mechanisms or files, it becomes hard to predict outcomes and easy to introduce unintended interactions.

3. Local changes must not silently alter global behavior.
Architecture should make cross-impact explicit, so adding one rule cannot unknowingly change unrelated safety outcomes.

4. Critical assumptions should be explicit and testable.
If correctness depends on hidden invariants, encode those invariants as checks and automated tests.

5. Interaction testing is as important as feature testing.
Testing single conditions is not enough; most high-risk failures emerge from combinations and precedence conflicts.

6. Change review should focus on behavioral impact, not only code quality.
For safety logic, every change should answer: what did this newly override, what can now override it, and what fallback path changed.

7. Runtime decisions should be explainable after the fact.
Operational logs should capture requested decision, final decision, and why transformations occurred, so incidents are diagnosable.

8. System design should prefer explicit decision models over implicit fallthrough behavior.
When behavior is explicit, maintainers can reason about intent directly instead of reconstructing it from execution flow.