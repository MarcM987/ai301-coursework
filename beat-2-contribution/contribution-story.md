# Contribution: [Issue Title]

Path: `beat-2-contribution/contribution-story.md`

This file is Assignment 5, and it is graded at the path above; a copy kept anywhere else in
the repository is not read. **Keep every section header below under its exact name** — the
format criteria grade exactly that. Your course repo link is the whole submission: no tool
files and no evidence uploads are part of Assignment 5.

**Contribution Number:** [1]
**Student:** Marc Martinez
**GitHub Username:** MarcM987
**Issue:** https://github.com/meshtastic/firmware/issues/8213
**Pull Request:** [GitHub PR link, once opened]

One repository, built across units 5 to 8, telling the whole story of your real
contribution. Fill it as you work, not at the end — the sections below ask for evidence that
is far easier to write down as it happens than to reconstruct in the last weekend.

Contribution Number stays `[1]` unless you make more than one contribution this term; it
just numbers them.

---

## Toolkit

Every story section below, from Why I Chose This Issue through Pull
Request, ends with a Toolkit block: which tool did that phase's work
and how you used it, what it produced, what difficulties or
shortcomings it presented, and what you changed or would change
because of them. Together the blocks are the thread the rubric's
Toolkit points read, and they are the raw material for your unit-9
portfolio, so keep them current as you work rather than
reconstructing them later.

A Toolkit block looks like this (copy it into each story section and
fill it there):

```text
**Toolkit**

- Tool: [which tool did this phase's work, and how you used it]
- What it produced: [described in a sentence or a short excerpt]
- Difficulties: [what fought you or fell short, or "none met"]
- What changed: [the patch, revision, or workaround, what you would
  update, or "nothing"]
```

This section also keeps one short dated entry per week of tool work,
starting below: what you built or changed that week, what broke, and
what you changed because of it. The blocks tell the story where it
happened; these entries are the toolkit's own timeline.

All four entries are graded. Keep every heading below, and fill each
one in the week it belongs to.

**Unit 5: Built the issue-scout overlay and a profile-driven search strategy for first contributions in the wild**

I built the scout using search requests that gather all things compatible with my profile, at least one search per profile sentence; this was a search for literal compatibility.
Then I decided the ranking of those results by the content of the profile, setting preferences for my strengths and desired work using words likely found in each subject to match: strongest in C/Python, growth goals in C++/assembly, signals/security, computer vision, and data science. 
I also made sure to drop any results with assignees or those that seemed stale; and ordered by fewer comments first, but with at least one comment.
What broke was the unaticipated inclusion of repo forks, throw away repos, and issues requiring hardware, so what changed was a revision of the rubric and evidence guide to account for each directly.


**Unit 6: Installed the voice-guard overlay, patched the rubric, and wrote a local repo-memory file for meshtastic/firmware**

[2-4 sentences: the voice-guard, the repo-memory file. What broke or
fell short, and what changed because of it. "Nothing broke" counts when
it is true - say how you know.]

Promoted the voice guard as instructed then created the repo-memory file with guidance on the contribution policy, test requirements, scope, and relevant subsystem.
I gave the memory file my current insights regarding the specifc location of behavior as well based on my reproduction and other issue comments.
I also made sure to add a note to keep the work honest and properly styled.


**Unit 7: [one line on the tool work]**

[2-4 sentences: the ship-gate and your gate manifest. What it produced
on your real branch, what fought you, what changed because of it.]

**Unit 8: [one line on the tool work]**

[2-4 sentences: the PR-monitor and your playbook. What it read, what it
drafted, what you did with the draft.]

---

## Why I Chose This Issue

I searched for this issue using the AI301 Issue Selection tool as required. 
However, I filtered for languages I was familiar with, issues specific to bugs, and organizations that I know and support.
My scan surfaced that I should double check that this is still an issue as the devlopment branch is on a newer version, which I subseqently did confirm on the latest release.
My scout produced an accept verdict on the issue. 
This issue also fits my profile because it plays on my strengths: C/C++ and Python, while also aligning with my profile's interest in security.
That is essentially what I hope to gain from working on this issue, using what I know while simultaneously pushing my comfort zone to grow, in this case towards security which is an area I'm hoping to grow in.

The scout did fairly well in all areas, until I created an interesting edge case for it.
A previous issue I was exploring proved to be already resolved during my reproduction and the maintainer agreed, so the tool had to contend with passing or failing an issue that I commented on, resolved, and was confirmed by the maintainer and discussed to be closed. 
My rubric was never meant to deal with the confusion of "no assignees" (informal or formal), but also informally resolved by the me, the user; It was also never meant to grade closed issues; it passed, with no evidence on assignees, arguably it should have failed on both metrics.
Both of these are edge cases that I would consider in my rubric, adding a check both to ensure the issue is open and also not informally resolved, even without a specific "claim".

Claimed: https://github.com/meshtastic/firmware/issues/8213#issuecomment-6423112343

**Toolkit**

- Tool: issue-scout (Patched for the wild according to unit 6, search-strategy.md to check for issues specific to my profile + rubric.md to check validity of the repo and the issue), I used it to both find issues that may be relevent to my skillset and interests and also to then grade issues that I select from curation.
- What it produced: It produced a verdict of accept for this issue and noted that it fits my desired growth areas to help me improve in both C++ and Security regarding its references to SSL certs. It gave it the difficulty of "Straightforward".
- Difficulties: It didn't handle the edges cases of already resolved issues very well for the other issues.
- What changed: The difficulty adjustment in scope via the patch. And I would update both the rubric and the evidence guide to consider scernios more common to resolved issues and not just the behaviors around open issues.

---

## Understanding the Issue

**Problem Description**

[In your own words, what is broken or missing?]

**Expected Behavior**

[What should happen?]

**Current Behavior**

[What actually happens?]

**Affected Components**

[Which parts of the codebase are involved?]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Reproduction Process

**Environment Setup**

[What a stranger would need to stand this up: your operating system,
the relevant versions (language, runtime, package manager, the project
itself), and how you set the project up. Then the challenges you faced
and how you solved them, or that none came up.]

**Steps to Reproduce**

1. [Step 1]
2. [Step 2]
3. [Observed result]

**Reproduction Evidence**

- **Commit showing reproduction:** [link to commit in your fork]
- **Screenshots/logs:** [if applicable]
- **My findings:** [what you discovered during reproduction; an
  honest, evidenced cannot-reproduce that led you to re-pick or ask
  the maintainer belongs here and costs you nothing]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Solution Approach

**Analysis**

[Your analysis of the root cause: what is causing the issue, traced
to the files and functions involved.]

**Proposed Solution**

[High-level description of your fix approach, and what you are
deliberately NOT changing.]

**Implementation Plan**

1. [Modify file X to do Y]
2. [Add or change Z]
3. [Update tests]

[Record deviations here as they happen: what changed mid-build and
why. A recorded deviation is honest work; silent drift is not.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Testing Strategy

[What observable checks prove the fix: your reproduction steps re-run
against the built change (before and after), and the repo's own test
suite or checks with the outcome shown. "Tests pass" with nothing
observable named is not a strategy.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Implementation Notes

[A running log, added to as you work. Date each entry. What you
built, decisions you made when you made them, wrong turns included.]

**[Date]**

[Entry]

**[Date]**

[Entry]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Pull Request

**PR Link:** [GitHub PR URL when opened]

**PR Description:** [what the PR says; much of the content above
adapts into it]

**Maintainer Feedback:**

- [Date]: [feedback received, or "none yet"; silence is a normal
  state and costs you nothing]
- [Date]: [how you addressed it]

**Status:** [Awaiting review / Iterating / Merged / Closed. The
status is a fact you record, never a grade: the PR is graded as
opened.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Learnings and Reflections

**Technical Skills Gained**

[What you learned technically, named concretely.]

**Challenges Overcome**

[What was hard and how you solved it; point at the real events, the
Toolkit blocks above are full of them.]

**What I'd Do Differently Next Time**

[Reflection on your process.]

---

## Resources Used

[What actually helped, not a reading list. List things this story
already shows you using: the doc you followed to set the environment
up, the thread that explained the bug, the person who answered you.
One real entry beats ten plausible ones.]

- [Link to documentation that helped]
- [Discussion, issue, or post that helped]
