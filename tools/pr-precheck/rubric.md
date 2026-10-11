# Rubric: is this pull request ready to submit?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Plan-Fidelity | evidence-guide "Plan fidelity" | Pass if every changed behavior is inside the plan's stated scope and every element of the plan is evident in the behavior, or otherwise mentioned in the deviation note or description. Fail on silent extra work with no explanation, or on a description that mentions a planned change the diff does not contain | required |
| Test-Evidence | evidence-guide "Test evidence" | Pass if the plan's reproduction steps were followed and the expected after fix outcome is present, not just mentioned. If the reproduction failed or repo test failed, but is mentioned this still passes. Fail if test evidence is not provided, was tested with a diff showing no changes, or does not reference a repro's relevant test if one is present | required |
| Diff-Review-able | evidence-guide "Diff quality" | Pass if the fix is in the diff and the diff has no left over debris. Fail if the change is not present or buried in other changes or debris | required |
| Standards-Honored | evidence-guide "Standards and comms" | Pass if every section the stated template requirements with relevant content to that template section, along with AI-use disclosure present when required by policies; if not required AI-use disclosure being present or absent does not affect the check grade. Fail on skipped sections, sections with irrelevant content, or ignored maintainer directions | required |


## Verdict rule

Accept if every required check passes.
Reject if any required check fails or is unclear.
Preferred checks are reported, but never change the verdict whether they pass or fail.
Unclear means the evidence review for that check was absent or indeterminate, and counts as fail.
