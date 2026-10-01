# Rubric: is this reproduction package ready to post?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
|Environment-recorded | Environment information in the repro report or drafted repro comment | the environment in the repro report matches the environment in the issue or address why they are different. And contains tool versions and OS version | required |
| Steps-repoduceable | Steps for reproduction in the repro report or drafted repro comment | the steps pass if they can be directly followed using only the public repository, the issue details, repro report, explains file implementations with no unexplained private files, with no statements that require unnamed steps unless those steps are to a common standard | required |
| Behavior-demonstrated | Behavioral artifact information in the repro report or drafted repro comments | the pasted logs, errors, outputs, or other artifacts show the same behavior described in the issue, or include matching descriptions as to why they are different | required
| Honest-report | Output descriptions in claim comments, repro report, or drafted repro comment compared with artifact behavior output | the stated results or descriptions do not contradict the include logs, output, or other artifacts, including if the issue was unable to reproduce as long as it is supported by the included artifacts. If a claim is made that is not support by evidence, then this fails | required
| Communication-follow-rules | Claim comments, repro report, or draft repro reports compared with the repository policies or policies listed in repo facts | the statements made follow every rule outlined in the policy and all required disclosure have been made | required |
| Communication-no-promises | claim comments or repro report| no promises of completion date, times, or performance nor statements that otherwise make guarentees about progress | required |

## Verdict rule
All required checks must pass for the verdict to be accepted.
If a required check fails or is unclear, then the verdict is to reject.
Unclear checks are treated as fails.
Checks that are preffered may pass, fail, or be unclear and will never affect the verdict.
