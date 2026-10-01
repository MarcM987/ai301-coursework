# Unit 3 — Plan and Build

Path: `beat-1-sandbox/unit-3/plan-and-implement.md`

Record of your plan, the branch you built it on, and the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in the
repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Posted upstream

**GitHub username**

MarcM987

**Plan comment**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/72#issuecomment-5939898687

`verify_password("password", "not_a_valid_bcrypt_hash")` raises `passlib.exc.UnknownHashError` instead of returning `False`, but valid hashes return correctly. This is passlib's error being passed through to the function without being caught.
My plan solves this issue by essentially catching the error in `verify_password()` in `core/security.py` to return `False` properly as expected, but does not catch any other errors to refrain from effecting behaviors or issues outside of this specifically.
Then I will remove the H-05 from `tests/unit/test_security.py` and check that `pytest tests/unit/test_security.py::TestSecurity::test_verify_with_wrong_hash_format -q` passes.
Will update with deviations if the plan needs to change.

## Your branch

**Branch**

fix/72-verify-password-unknown-hash

**Evidence**

[Your Unit 2 reproduction steps re-run against the built change: the before, then the
after. Paste both, including the commands you ran and their output.]

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

Run-Score: First- 19/20, Second- 20/20, Third- 18/20, Fourth- 20/20, Fifth- 20/20

**Package analysis**

pkg-20, my rubric decided to reject this pkg which agrees with its gold label. However, this was not without a bit of headache, as it seemed to be on the edge, sometimes accepting. The rubric had its requirement clear regarding AI disclosure, the evidence guide had the relevant family to pair with it as well, but my procedure guide never directly collected the evidence requiring it. Hence the more runs than usual, this package kept flipping no matter how I changed my rubric, but once I fixed the skill's procedure, the rubric's evaluation became consistent and properly noticed the missing disclosure.

**Check rationale**

| Communication-conventions | the plan and plan comment compared against the issue thread, thread highlights, repo facts, and contribution policy and AI policy | the plan and comment follow all required formatting and inclusions required as well as providing ai disclosures when required by policies | required |

This reads as it does because originally I simply required that all contributions and AI policies must be followed, but this was not direct enough and it kept missing the ai disclosure. While this was also an issue with my procedure, simply telling it to 'follow required policies' is not direct enough. It should be stated the aspect of those policies to precisely review each requirement. It needs to be clear for example, that AI disclosures must be present if required, while also ensuring that disclosures where not required don't create a failure.

**Trade-offs**

The trade off with this check in its current form is that it also restricts the plan and were fail when the plan itself doesn't make ai disclosures, even though this is not strictly required. However, as a personal preference, it's important to be upfront about ai usage even for ourselves. If part of my plan involves using ai or I deviate from the plan because of ai, this should be clearly documented, so that approach reasoning, understanding, and output behavior confidence remain clear.

---

Related paths: `plan.md` and `eval-run.txt` in this directory; your skill's files in
`tools/plan-check/`.
