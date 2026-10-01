# Rubric: is this plan ready to post and build from?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Diagnosis-grounded | The plan's stated diagnosis compared against the repro evidence and issue body | the stated cause is present, explains the actual behavior the repro shows, and does not contradict any artifacts or evidence | required |
| Scope-bounded | The plan's description and scope compared against the issue | the plan stays within the scope of the issue and does not reference changes outside of the scope of that issue | required |
| Approach-followable | the plan's description and changes | a stranger should be able to follow the plan without needing to clarify the approach | required |
| Test-specific | The plan's test plan compared against the repro evidence | the test plan should specifically involve testing the change in behavioral outcome described in the evidence | required |
| Honesty-risks | the plan's risk and unknowns, if present | if the plan has uncertainty, that uncertainty is directly addressed. or the plan has no uncertainty mentioned | required |
| Communication-conventions | the plan and plan comment compared against the issue thread, thread highlights, repo facts, and contribution policy and AI policy | the plan and comment follow all required formatting and inclusions required as well as providing ai disclosures when required by policies | required |
| Communication-maintainer | the plan and plan comment compared against the issue thread and thread highlights | if the maintainer or owner mentions any specific directions regarding the issue, the plan or plan comment must address that issue | required |

 


## Verdict rule
Accept if every required check passes.
Fail if any required check fails or is unclear.
Preferred checks never change the verdict.
All unclear checks count as failed.

