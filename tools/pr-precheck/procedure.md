# Procedure: how this tool grades a PR package

## Read order

1. Decide the mode. A bundle, or a bundle id (e.g. 'pkg-07' or 'calib-01'), is eval mode. Anything else is live mode.
2. In live mode only, read 'scope.md' first. Stop with no verdict if the 'Repo:' line is still a placeholder, or if the issue or PR is outside that repo.
3. Read the issue context (eval: the Issue block and thread highlights; live: the issue body and thread). 
    Note the requested behavior and any maintainer direction.
4. Read the repo standards (eval: the repo-facts section; live: '.github/PULL_REQUEST_TEMPLATE.md' and 'docs/CONTRIBUTING.md').
    Note template sections and any AI-use or checklist ask.
5. Read the plan (eval: the plan-context section; live: 'plan.md', including '## Deviations'). 
    Note in-scope, out-of-scope, test plan, and deferred sections.
6. Read the candidate PR: title, description, commits, unified diff, and test evidence (live: 'pr_draft.md', 'git diff main...HEAD', 'test_evidence.md').
7. Read 'references/evidence-guide.md' then and only then the 'rubric.md' before grading. 
    Do not grade from memory of a previous run.
8. In live mode only, read 'voice-guide.md'. 
    Hold it for the the summary as it is not a check.

## Evidence gathering

1. Title: quote the title and the issue's requested change.
2. Plan fidelity: quote the plan's in-scope and out-of-scope lines, any deviation note, the diff's changed files, and any description sentence that mentions the plan was followed, deviated from, or that a file was updated.
3. Test evidence: quote the plan's test plan steps and the matching before/after lines in the test evidence section. 
    If the planned reproduction is absent, quote that absence.
4. Diff quality: quote the changes that implement the fix and any debug print, commented-out block, dead function, TODO, or unrelated hunk. 
    If no changes, quote that fact.
5. Standards: quote each template section in the repo facts (or live template) requires, and the matching or missing text in the PR or description. 
    If there is no template, quote that fact and quote AI-use policy only if one is explicitly required.

## Check execution

1. Run the checks in rubric table in order they are listed.
2. For each check, compare the gathered evidence and quotes for that check's evidence family to that check's pass condition. 
    Do not re-read the whole package between checks.
3. Grade checks only as pass, fail, or unclear; Unclear means the evidence was absent or indeterminate.
4. An incomplete check row fails. 
    If the incomplete check mentions it is required or preferred, that check's failure is treated accordingly.
    If the incomplete check does not mention whether it is required or preferred, it is considered required and that check's failure is treated accordingly.
5. In live mode, voice guide breaks are summary notes only and are not checks unless the rubric has a check that refers to the voice guide specifically.

## Verdict assembly

1. Apply the verdict rule in 'rubric.md' exactly. 
    Accept only if every required check passed and reject otherwise; Unclear counts as fail.
2. Print one summary line per failed check: the check's name, the grade it received, and the quote that decided it.
    In live mode, add voice guide notes after the check lines.
3. End with the fenced JSON block from 'SKILL.md' and print nothing after it. 'item' is the PR URL in live mode, or the bundle id in eval mode.
