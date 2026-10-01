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

Files used both before and after the fix:

**'good_test.py'**
```python
from core.security import hash_password, verify_password
hashed = hash_password("password")
print("hash:", hashed[:7], "...")
print("correct password:", verify_password("password", hashed))
print("wrong password:  ", verify_password("nope", hashed))
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

- Before:

Run validating good behavior.

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

Run validating bad behavior.

```bash
python3 bad_test.py
```
```bash
passlib.exc.UnknownHashError
hash could not be identified
```

Problem confirmed by test result with H-05 marker:
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

- After:

Run validating good behavior is still correct

```bash
python3 good_test.py
```
```bash
(trapped) error reading bcrypt version
Traceback (most recent call last):
  File "/Users/marc/Desktop/CodePath/AI301_2026/pathreview-ai301-fa26-s1/.venv/lib/python3.14/site-packages/passlib/handlers/bcrypt.py", line 620, in _load_backend_mixin
    version = _bcrypt.__about__.__version__
              ^^^^^^^^^^^^^^^^^
AttributeError: module 'bcrypt' has no attribute '__about__'
hash: $2b$12$ ...
correct password: True
wrong password:   False
```

Run validating bad behavior is fixed

```bash
python3 bad_test.py
```
```bash
returned: False
```

Fix confirmed by test result with removed H-05 marker:
```bash
pytest tests/unit/test_security.py::TestSecurity::test_verify_with_wrong_hash_format -q
```
```bash
::test_verify_with_wrong_hash_format -q
.                                                                                                  [100%]
============================================ warnings summary ============================================
core/config.py:7
  /Users/marc/Desktop/CodePath/AI301_2026/pathreview-ai301-fa26-s1/core/config.py:7: PydanticDeprecatedSince20: Support for class-based `config` is deprecated, use ConfigDict instead. Deprecated in Pydantic V2.0 to be removed in V3.0. See Pydantic V2 Migration Guide at https://errors.pydantic.dev/2.13/migration/
    class Settings(BaseSettings):

-- Docs: https://docs.pytest.org/en/stable/how-to/capture-warnings.html
1 passed, 1 warning in 0.23s
```
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
