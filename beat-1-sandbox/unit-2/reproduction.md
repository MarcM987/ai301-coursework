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

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/72#issuecomment-5863014662

Hello, I'd like to work on this issue, #72, as my first contribution to this repo. verify_password currently raises UnknownHashError when a hash is in a bad format. I'll reproduce the issue and update with a reproduction report with my environment, reproduction steps, and the output behavior.
Then I'll get to work on the fix, removing the xfail marker referencing H-05 once it's working.

**Reproduction comment**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/72#issuecomment-5863022991

# Reproduction Report
Successfully reproduce. verify_password raises passlib.exc.UnknownHashError instead of False when given a hash in a bad format.

## Environment
macOS 15.7.7 (x86), Python 3.14.7, repo at commit f89c06f
passlib 1.7.4, bcrypt 4.3.0 

Note about the environment, function was run isolated instead of re-building the entire project.
Not all dependencies were used

## Reproduction Steps

1. Install and environment creation

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
pip install -e . --no-deps
pip install \
  "passlib[bcrypt]>=1.7.4" \
  "bcrypt>=4.0.1,<5.0.0" \
  "pydantic>=2.5.0" \
  "pydantic-settings>=2.1.0" \
  "python-jose[cryptography]>=3.3.0" \
  pytest
```

2. Verify Correct Behavior

```bash
python3 good_test.py
```
```bash
(trapped) error reading bcrypt version
Traceback (most recent call last):
  File "/Users/marc/Desktop/CodePath/AI301_2026/Unit 2/pathreview-ai301-fa26-s1/.venv/lib/python3.14/site-packages/passlib/handlers/bcrypt.py", line 620, in _load_backend_mixin
    version = _bcrypt.__about__.__version__
              ^^^^^^^^^^^^^^^^^
AttributeError: module 'bcrypt' has no attribute '__about__'
hash: $2b$12$ ...
correct password: True
wrong password:   False
```

**'good_test.py'**
```python
from core.security import hash_password, verify_password
hashed = hash_password("password")
print("hash:", hashed[:7], "...")
print("correct password:", verify_password("password", hashed))
print("wrong password:  ", verify_password("nope", hashed))
```

3. Reproduced Issue

```bash
python3 bad_test.py
```
```bash
passlib.exc.UnknownHashError
hash could not be identified
```
**'bad_test.py'**
```python
from core.security import verify_password
try:
    result = verify_password("password", "not_a_valid_bcrypt_hash")
    print("returned:", result)
except Exception as e:
    print(type(e).__module__ + "." + type(e).__name__)
    print(e)
```

## Expected
verify_password("password", "not_a_valid_bcrypt_hash") returns False and does not raise. 

## Actual
passlib.exc.UnknownHashError is raised

Additionally Verified the XFAIL with H-05

```bash
pytest tests/unit/test_security.py::TestSecurity::test_verify_with_wrong_hash_format -v --tb=short -rx
```
```bash
======================================================================================== test session starts ========================================================================================
platform darwin -- Python 3.14.7, pytest-9.1.1, pluggy-1.6.0 -- /Users/marc/Desktop/CodePath/AI301_2026/Unit 2/pathreview-ai301-fa26-s1/.venv/bin/python3.14
cachedir: .pytest_cache
rootdir: /Users/marc/Desktop/CodePath/AI301_2026/Unit 2/pathreview-ai301-fa26-s1
configfile: pyproject.toml
collected 1 item                                                                                                                                                                                    

tests/unit/test_security.py::TestSecurity::test_verify_with_wrong_hash_format XFAIL (issue #72 (manifest H-05): password verify raises UnknownHashError instead of returning False)           [100%]

========================================================================================= warnings summary ==========================================================================================
core/config.py:7
  /Users/marc/Desktop/CodePath/AI301_2026/Unit 2/pathreview-ai301-fa26-s1/core/config.py:7: PydanticDeprecatedSince20: Support for class-based `config` is deprecated, use ConfigDict instead. Deprecated in Pydantic V2.0 to be removed in V3.0. See Pydantic V2 Migration Guide at https://errors.pydantic.dev/2.13/migration/
    class Settings(BaseSettings):

-- Docs: https://docs.pytest.org/en/stable/how-to/capture-warnings.html
====================================================================================== short test summary info ======================================================================================
XFAIL tests/unit/test_security.py::TestSecurity::test_verify_with_wrong_hash_format - issue #72 (manifest H-05): password verify raises UnknownHashError instead of returning False
=================================================================================== 1 xfailed, 1 warning in 0.29s ===================================================================================
```


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
