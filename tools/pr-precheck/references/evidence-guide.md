# Evidence guide: where evidence lives in a PR package

## Plan fidelity (harness category: silent-drift)

Where it lives:
- Eval: the plan-context block's in-scope lines, not-in-scope lines, files, and any deviation or deferral note; 
    the candidate PR's diff and commit list; 
    fidelity sentences in the description (such as "as planned", "no other changes", "docs updated", or any other statements to that affect).
- Live: 'plan.md' Scope and '## Deviations'; 'git diff main...HEAD'; fidelity sentences in 'pr_draft.md'.

What good looks like:
Every changed file sits inside the plan's boundary, or is named in a deviation note or mentioned in the description. 
Every planned change is in the diff, or the deviation note or the description say it was left out and why. 
Silent drift is extra or less work than the plan requires with no note, or a description that mentions a change the diff does not contain. 
An honest mention in both places is not drift.

## Test evidence (harness category: not-tested)

Where it lives:
- Eval: the plan context test plan, the repro steps it mentions, and the candidate PR's Test evidence section.
- Live: 'plan.md' Test Plan; 'test_evidence.md' (along with the 'make test-unit', 'make test-integration', 'make lint', and 'make typecheck' output).

What good looks like:
The planned repro was run and the expected outcome is visible in output. 
If the reproduction failed or a test failed, but that fact was mentioned, it still passes. 
Skipped reproduction, reproduction without evidence, or a test run on an unchanged-path (a diff with no changes) fail.

## Diff quality (harness category: unreviewable)

Where it lives:
- Eval: the candidate PR's unified diff and commit list.
- Live: 'git diff main...HEAD' and 'git diff main...HEAD --stat'.

What good looks like:
The fix is visible in the planned files, the diff has no debris (debug prints, commented-out experiments, TODO mentions, dead code, formatting churn, or a drive-by edits) in a file the plan did not name.

## Standards and comms (harness category: standards-wall)

Where it lives:
- Eval: the repo-facts block's PR-template asks, contributing policy mentions, and any AI-use policies; the description's sections; thread highlights for a maintainer ask.
- Live: '.github/PULL_REQUEST_TEMPLATE.md', 'docs/CONTRIBUTING.md', the issue thread (including any direction from the maintainer), and the filled sections of 'pr_draft.md'. 

What good looks like:
Every section the stated template asks is filled with the relevant content, the issue link is present when asked, and AI-use is disclosed when policies requires it. 
No policy for a disclosure means a missing disclosure is not a fail. 
Leftover boilerplate, a skipped required section, or an ignored maintainer ask or direction is a fail. 
Whether the description's claims match the diff is plan fidelity, not this family.

