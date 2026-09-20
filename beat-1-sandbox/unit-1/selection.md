# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/72

**Verdict output**

[Your skill's live-mode output for this issue, pasted verbatim and ending with the
fenced JSON verdict block. A summary does not satisfy this field.]

**The verdict must record `accept` for this issue.** Choose an issue your own skill
accepts. If your skill rejects every candidate you try, that is a signal about your
rubric rather than about the issues: revise it and re-run — retries are unlimited and a
partial re-run costs about $0.20 — or run the skill on different candidates. Output
recording `reject` for the issue you chose earns no credit for this field.

```
All four repo-level checks are shared (today 2026-09-19, live mode):

- Maintained-recent — last 5 main commits: 2026-09-16 ×3, 2026-08-24 ×2 → all inside 90 days.
- Active-releases — latestRelease: null, repo has no releases yet → the condition's second branch.
- Active-open — isArchived: false.
- Allows-AI — docs/CONTRIBUTING.md (189 lines, 14 headings) has no AI clause; no AI_POLICY.md/AI_USAGE_POLICY.md; PR template asks only for CI-green + xfail removal. Silence passes.

Repo-wide, gh pr list --state all returns [] — zero PRs exist, so no issue here can have a linked open PR or an abandoned attempt. All three issues have assignees: [] and 0 comments.

Ranked read-out — all three accepted

1. #72 — verify_password raises UnknownHashError on malformed hashes (best fit)
Python, and it sits in core/security.py — squarely in the security area you named as a growth goal. It's the only tier-1 / good first issue of the three, 1–2 hours, two files, and the covering test already exists as a strict=True xfail keyed to manifest H-05, so the fix verifies itself the moment CI flips green. Smallest blast radius of the three for a first PR.

...

Per-check detail: every required check passes on all three. The only non-pass anywhere is the preferred Issue-reproduceable-steps on #32 — which by the verdict rule cannot change the outcome, and only cost it rank.

One note on the house rule: it would have mattered if classmates had claimed these, but all three threads are empty, so Issue-available-not-comment-claimed passes on its own terms rather than by the classroom exemption.
 {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/72",
    "checks": [
      {"name": "Repository-maintained-recent", "grade": "pass", "evidence": "Last 5 main commits: 2026-09-16 x3, 2026-08-24 x2 — all within 90 days of 2026-09-19"},
      {"name": "Repository-active-releases", "grade": "pass", "evidence": "gh repo view returns latestRelease: null — repo has no releases yet"},
      {"name": "Repository-active-open", "grade": "pass", "evidence": "gh repo view returns isArchived: false"},
      {"name": "Repository-allows-AI", "grade": "pass", "evidence": "docs/CONTRIBUTING.md has no AI clause and no AI_POLICY.md exists; silence passes"},
      {"name": "Issue-scope-clear", "grade": "pass", "evidence": "\"lets passlib's UnknownHashError escape... should fail closed (return False), not raise\" — one behavior, 0 comments, no debate"},
      {"name": "Issue-scope-design", "grade": "pass", "evidence": "Labeled 'bug'; a fail-closed correctness fix, not a product or design choice"},
      {"name": "Issue-scope-support-request", "grade": "pass", "evidence": "Opened by maintainer Aburke225 as a defect report, not a usage question"},
      {"name": "Issue-scope-history", "grade": "pass", "evidence": "gh pr list --state all returns [] repo-wide; 0 abandoned attempts"},
      {"name": "Issue-available-not-assigned", "grade": "pass", "evidence": "assignees: []"},
      {"name": "Issue-available-not-worked", "grade": "pass", "evidence": "No linked PRs in timeline and 0 comments; no PRs exist in the repo at all"},
      {"name": "Issue-available-not-comment-claimed", "grade": "pass", "evidence": "Comment count is 0, so no maintainer has granted it to anyone"},
      {"name": "Issue-reproduceable-steps", "grade": "pass", "evidence": "\"The covering test is marked @pytest.mark.xfail referencing manifest id H-05\" — names the test that reproduces it"}
    ],
    "verdict": "accept"
  }
```

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

Run Scores:
First run - 11/20, second run - 16/20, third run - 18/20, fourth run - 19/20, final run - 20/20

**Issue analysis**

issue-06:

rubric's decision - accept

gold label - accept

rubric's reasoning - the rubric accepted this issue because it passed every criteria, including the preferred checks. It comes from a repository with no releases yet, but with recent commits. The issue's is scoped to one clearly defined problem. And the issue is neither formally assigned or informally claimed in the comments with not history of multiple abandoned PRs that indicate hidden issues. 

**Check rationale**

| Issue-available-not-comment-claimed | Claim comments | the maintainer has not given the issue as a reply to someone requesting it in the comments | preferred |

Reasoning- 
Sometimes people attempt to claim issues in the comments of the issue instead of submitting proper requests and this check looks for that.
However, just because someone comments they want the does not mean the maintainer will assign it to them, so it also checks whether or not the
maintainer agrees that the issue is theirs. The check is listed as 'preferred' though so that the rubric does not disqualify the issue if it has
been abandoned or unassigned with the comments remaining; there is a separate check in my rubric that checks for proper assignment and unlinked PRs 
separately as 'required' checks. This one is a courtesy check just incase, but does not disqualify for comments that happened potentially years ago 
that may not still be relevant.

**Trade-offs**

This check in its current revision is a preferred check with specific instructions not to change the verdict, 
so it should not change the verdict grading of the issue, but it will affect the ranking. Originally, the check
was required and it falsely flagged issues that had old abandoned comment claims from years ago and I adjusted the weight to
preferred to allow for those scenarios. This means the check may seem to allow the passing of a comment claimed issue, but there
are multiple other checks for catching claimed issues already as redundancy.

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

1. The issue fits my interest because it involves a language I'm strongly familiar with, Python, and covers a topic and tool set I that not only have experience in, but also want to do more of.
2. The verdict correct identified this issue as accepted and also correctly ranked it as number 1, which aligns with my preferences. However, something I weighted for the issue that the rubric could not was that using issues is a topic I specifically need to review more and this would be great practice for reenforcing that area; this only came to mind once I came across the specific issue, and if I did not preemptively consider that then neither would my rubric.
3. I anticipate this may have a fair amount of difficulty in claiming primarily because there are likely many people who also want to claim it. Its interesting, challenging, but not too challenging, involves the 'cool' world of security, and is marked as a 'good first issue', which means the competition for claiming the issue is likely higher than the others.

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
