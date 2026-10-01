# Procedure: how this skill grades a plan package

## Read order

1. If live mode, read scope.md first. Stop if the issue is not in the scoped repo or if the repo line is still a placeholder
2. Read the issue body and thread (or thread highlights if in eval mode). Note the requested behavior and any maintainer directions
3. Read the repro repro evidence. Note the actual and expected behaviors.
4. Read the candidate plan. Note the plan's described cause, scope, steps, tests, and any risks.
5. Read the candidate plan comment.
6. Read rubric.md, references/evidence-guide.md, and this procedure before grading. Do not grade on memory of previous runs.

## Evidence gathering

1. Diagnosis: quote the plan's cause and the repro's actual behavior
2. Scope: quote the plan's in scope and out of scope sections
3. Executability: quote the named files, code, and changes
4. Test: quote the test plan's outcomes and the matching repro steps
5. Honesty: quote the stated risks/unknowns/deviations mentioned in the plan, or the fact that it is missing
6. Comms: quote the thread (or thread highlights) and repo policies (or repo facts) with the matching or missing phrases in the the plan or plan comment relevant to those policies.

## Check execution

1. Run the checks in the order as they are provided in the rubric's table.
2. For each check, compare the gathered evidence for that check to its pass condition.
3. If a check row is incomplete or only partially filled, it fails. Unless stated as preferred, it is treated as required.
3. Grade pass, fail, or unclear. Unclear means the evidence was absent or indeterminate.
4. Do not re-read an entire package between checks, unless that is in dispute. Use the gathered evidence.
5. Voice guide rules in live mode are notes only and are not checks unless directly referenced in the rubric.

## Verdict assembly

1. Apply the rubric verdict rule exactly.
2. If any check is unclear it is counted as a failure
3. A failed or unclear check, whether preferred or required, gets reported
4. Provide a one-line summary for each check
5. Provide a json block with the item graded, the checks and their results, and the verdict. Print nothing else after this.
