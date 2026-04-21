## System Improvements

To avoid choosing a failsafe action based purely on implicit control flow, the system should define an explicit policy table that maps failure conditions to permitted failsafe actions. The actions themselves should be represented as named enum values, and selection should depend on the policy rather than on enum ordering.

The decision process should not be split across multiple places such as per-failure mapping helpers and a fallthrough chain. Instead, policy, eligibility checks, and fallback selection should be centralized in one implementation point. A single loop over explicitly permitted actions is safer and clearer than relying on switch-case fallthrough, because it reduces hidden coupling and makes regressions easier to detect.