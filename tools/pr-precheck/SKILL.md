---
name: pr-precheck
description: Grade a PR package (a candidate pull request read against the plan it claims to implement and the issue that plan belongs to) and decide whether it is ready to submit. Use when checking your own branch, draft PR title, and description before opening the pull request, or when grading an eval package bundle.
---

# pr-precheck: rubric-driven PR grading

## The question

You grade one Pull Request package to answer one question: is this PR ready to submit?
A PR package is a candidate pull request, including a title, description, commits, diff, and test evidence.
The PR package is to be read against the plan it claims to implement and the issue that plan belongs to. 
Do not answer based on your opinion, specifically Execute 'procedure.md' which will apply 'rubric.md' to evidence which will be located by 'references/evidence-guide.md'

Decide accept (ready to submit) or reject (hold) for one PR package.
Do not grade additional packages in the same run.
Do not answer any other question (including, but not limited to: code quality, issue quality, or merge accept likelihood).

## Inputs and modes

- **Live mode.** The candidate submission checked before it is submitted.
    Read only these inputs: 'plan.md' (including any '## Deviations' notes), the branch diff from 'git diff main...HEAD' (three dots; committed changes only), the draft title and description in 'pr_draft.md', and 'test_evidence.md'. 
    Read them against the issue named in the command.
    Gather issue-side evidence from the scoped repo: the issue thread, '.github/PULL_REQUEST_TEMPLATE.md', and 'docs/CONTRIBUTING.md'.
    A house-chain student uses the house plan and the house repro pack; the same checks grade the same things. 
    If a named live file is missing, say which file is missing and refuse to grade.
- **Eval mode.** A PR package bundle is everything that is needed. 
    Read only the bundle text (issue context, repo-facts block, plan-context block, candidate PR title, description, commits, diff, and test evidence).
    Do not fetch GitHub, do not open other files, and do not use knowledge of the live issue. The 'source:' line is not a link to follow.
    Grade every check and apply the full verdict rule.

If the user message is an eval bundle, or names a bundle such as 'pkg-07' or 'calib-01', you are in eval mode. Otherwise, you are in live mode.

## The scope seam (live mode only)

In live mode, read 'scope.md' before anything else. 
It names the only repo this tool may grade and the rules of that scope. 
Refuse to grade a package whose issue or PR is not in that repo. 
If the 'Repo:' line still contains a placeholder (such as '<ORG>/<PATH-REVIEW-REPO>'), stop without grading and instruct the user to replace that line with the relevant repository. 
Never guess or assume the scope outside what is precisely mentioned.
In eval mode, ignore 'scope.md' entirely.

## The voice seam (live mode only)

In live mode, also read 'voice-guide.md'.
Hold the draft PR title and description against those rules and report broken rules, quoted, in the summary.
The voice guide never changes the verdict unless a rubric check explicitly requires it.
In eval mode, ignore 'voice-guide.md' entirely.

## Component reads

Read these files in the manner described in 'procedure.md' before grading:
- 'rubric.md: the checks table of criteria to hold to the PR and the corresponding verdict rule that grades it. 
    If it has no filled check rows, or incomplete check rows, stop and say this skill cannot grade without a complete rubric.
- 'procedure.md': the procedure laid out, what to do, the read order, evidence gathering, check execution, and verdict assembly. 
    If any of those headings have no steps, stop, and say this skill cannot grade without a complete procedure. 
    Follow the procedure as written with no deviation.
    If it is silent on a step, name the gap in the summary. Do not improvise around it.
- 'references/evidence-guide.md': where each evidence family lives in a bundle in live mode, and what good looks like.
    A rubric check with evidence this guide cannot locate is graded 'unclear'.

## Verdict and output

The verdict space is binary: 'accept' (ready to submit) or 'reject' (hold). 
There is no third verdict, if it is not confidently accept, then it is reject. 
Concerns go in evidence lines, and do not affect the verdict.

Print a short per-check summary first (one line per check, plus any live-mode voice notes). 
Then end with this fenced JSON block and nothing after it. 
Do not alter, extend, or reorder the schema in any way:
```json
{
  "item": "<PR URL or bundle id>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear",
     "evidence": "<one line: the fact or quote that decided it>"}
  ],
  "verdict": "accept|reject"
}
```
The skill harness parses the last fenced JSON block. 
It must be present, valid, and last. 
'item' is the PR URL in live mode, or the bundle id in eval mode.

## Grading discipline

- Evidence first: No check is graded without the fact or quote that decided it. 
    Opinions or "Looks fine" are not evidence.
- Grade the thing, not the polish: A short complete PR can be ready. 
    A long confident one can hide drift, so review thoroughly. 
    Read the diff, evidence, and description against the plan, issue, and provided or stated standards.
- Honest shortfalls are not silent drift: 
    A planned change that the plan's deviation notes and the description both refer can still pass. 
    A description that claims a change the diff does not contain cannot pass.
    A failing repo check pasted with its reason is evidence; A hidden or unexecuted plan is not.
- The rubric decides, not the run: If a check passes by its stated condition, but feels wrong for any other reason, it still passes. 
    The fix belongs in the rubric.
- The procedure decides how, not the run: Follow 'procedure.md' and report gaps instead of improvising steps.
- Unclear grades when the rubric verdict rule is silent defaults to fail: Treat 'unclear' as the verdict rule directs.
    Where that rule is silent, an unverifiable claim fails. 
    A package that cannot be verified is not ready to submit.
