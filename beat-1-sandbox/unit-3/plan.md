# Plan for issue #72 `verify_password` must fail closed on malformed hashes
## Diagnosis
`verify_password` in `core/security.py` calls `pwd_context.verify()` and lets passlib raise `passlib.exc.UnknownHashError` when the stored string is not recognized

## Repro Evidence Recap
Reproduced on macOS 15.7.7 (x86), Python 3.14.7, passlib 1.7.4, bcyrpt 4.3.0, commit f89c06f.
- Good Behavior: `verify_password(correct, valid_hash)` return `True`; if wrong password return `False`.
- Bad Bahavior: `verify_password("password", "not_a_valid_bcrypt_hash")` raises `UnknownHashError:...`
- Related test: `tests/unit/test_security.py::TestSecurity::test_verify_with_wrong_hash_format` is `@pytest.mark.xfail(strict=True, reason="issue #72 (manifest H-05): password verify raises UnknownHashError instead of returning False")` and wants `result is False`.

## Scope
Within Scope:
- `core/security.py` to be modified for catching unrecognized or malformed hashes inside `verify_password()` and returning `False` appropriately.
- `tests/unit/test_security.py` to remove the H-05 xfail marker on `test_verify_with_wrong_hash_format`.
Not within scope:
- Changes to the `hash_password()` function itself
- Changes to passlib or bcrypt versioning

## Steps and Approach
1. Wrap `pwd_context.verify()` with a try and except block to catch only `UnknownHashError`
2. On catch, return `False` while keeping return type `bool`
3. Remove the H-05 xfail marker in the relevant test.

## Test Plan
Re-run repro steps and note changed behavior has been corrected
1. `verify_password(correct, valid_hash)` still returns `True`, if wrong password return `False`
2. `verify_password("password", "not_a_valid_bcrypt_hash")` returns `False` and does not raise.
3. `pytest tests/unit/test_security.py::TestSecurity::test_verify_with_wrong_hash_format -q` passes (no xfail).
Expecting: no `UnknownHashError` on the malformed hash

## Risks/Unknowns
Other passlib errors may or may not need to also return `False`, this plan only catches `UnknownHashError` to keep within scope

## Deviations
No deviations, plan executed as specified and resolved the incorrect behavior.
