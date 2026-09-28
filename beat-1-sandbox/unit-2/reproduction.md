# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

Record of your claim and reproduction on the issue you chose in Unit 1, and of the
evaluation runs that produced `eval-run.txt`. This file is graded at the path above; a copy
kept anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your identity upstream

**GitHub username**

MarcM987

---

## Posted upstream

**Claim comment**

[Link to the comment where you claimed the issue. Use the comment's own permalink, not the
issue page on its own. **Then paste the text of that comment underneath the link** — the
pasted text is what this field is graded on, so copy across what you actually posted.]

Hello, I'd like to work on this issue, #72, as my first contribution to this repo. verify_password currently raises UnknownHashError when a hash is in a bad format. I'll reproduce the issue and update with a reproduction report with my environment, reproduction steps, and the output behavior.
Then I'll get to work on the fix, removing the xfail marker referencing H-05 once it's working.

**Reproduction comment**

[Link to the comment where you posted your reproduction. It must record the environment
(OS, relevant versions, code state), steps a stranger could follow, and what you observed.
**Then paste the text of that comment underneath the link** — the pasted text is what this
field is graded on, so copy across what you actually posted.]

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

Run Scores: First run- 18/20, Second run- 16/20, Third run- 20/20

**Package analysis**

issue-06:

rubric's decision - accept

gold label - accept

rubric's reasoning - the rubric accepted this issue because it passed every criteria, it has the environment properly specified, the reproduction steps clear (even though minimal), the issues behavior is clear and shown in the relevant artifacts, is honest with no statements contradicting the evidence presented in the artifacts, and the communication policy breaks no rules, and with no disclosure being required, the ai disclosure is not present. 

**Check rationale**

| Steps-repoduceable | Steps for reproduction in the repro report or drafted repro comment | the steps pass if they can be directly followed using only the public repository, the issue details, repro report, explains file implementations with no unexplained private files, with no statements that require unnamed steps unless those steps are to a common standard | required |

This step is meant to ensure the steps provided can be followed and reproduced by the reader. In its original form it actually failed this package due to env.yml as the original form of this check prevented any private files or files that are not provided. However, as this made me rethink this rule, I realized that this means files that are private like key secrets would make it fail and, more relevantly, explained basic environmental variables or explained standard minimum structures would also make it fail. For example, if you're in a web based repository working with html, testing against a simple minimum html file and state the only thing within is the doctype, header, and body symbols, it should be known what that entails. This is similar to this gold label accept case wherein the poster states "wrote a minimal env.yml containing a valid dependencies: list plus a category: section (the section conda does not recognize)". So I changed my rule to allow this, provided that the file is properly explained.

**Trade-offs**

There are clear tradeoffs with this specific check. Keeping this now refined version of the check means that scenarios that require more knowledge of the reader may increase; for example in pkg-05, I don't know what a "valid dependency" requires in a yml file. Allowing for this to pass as check also allows similar cases and more of the cases. It could potential result in little provided files contexts that are explained, but perhaps unclear to certain readers or readers unfamiliar with the language or topic at hand, as I am in this case. However, there is certainly the argument to be made regarding whether or not that person should be contributing unassisted to that particular issue, but with modern LLMs in their current state, this might not be a particularly strong argument today.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/repro-check/`.
