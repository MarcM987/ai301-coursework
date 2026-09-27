# Evidence guide: where proof lives in a reproduction package

## Environment
Where it lives: 
- Eval: the environment content (including version elements, such as tool version, build version, OS version, and commit identity) within the Candidate repro report
- Live: the environment content (including version elements, such as tool version, build version, OS version, and commit identity) within the drafted repro comment

What good looks like:
- The report contains version names, including OS, build, or tools, matched against those within the issue, or the difference and discrepancies called out and explained in plain words. (e.g. Issue: hyperfine 1.20.0, macOS 26.5, Report: hyperfine 1.20.0, macOS 26.5) or (e.g. Issue: hyperfine 1.21.0, macOS 26.5, my tool version is newer, but the changes mentioned in the changelogs since then don't affect the issue)

## Steps
Where it lives:
- Eval: the reproduction steps (to include the steps required to trigger the behavior as described in the issue) within the Candidate repro report.
- Live: the reproduction steps (to include the steps required to trigger the behavior as described in the issue) within the the drafted repro comment.

What good looks like:
- The steps contain followable actions or commands that can be clearly taken that lead to the behavior described in the issue or comment. (e.g. Step 1: echo "clear edge case input" | command Step 2: issue output observed)
- All requirements or files to complete the steps are publicly available, commonly known, explained, or not secret files on the posters machine. (e.g. Step 1: publicrepofile.txt | command Step 2: issue output or stated behavior observed)
- Steps taken match the steps as described within the issue.

## Behavior shown
Where it lives:
- Eval: logs, pasted output, screenshots, exit codes, or other concrete evidence (also known as artifacts) in the Candidate repro report with the issue's behavior shown. Not the caption explaining the behavior, only the shown behavior itself.
- Live: logs, pasted output, screenshots, exit codes, or other concrete evidence (also known as artifacts) in the drafted repro comment copared with issue's behavior shown. Not the caption explaining the behavior, only the shown behavior itself.

What good looks like:
- The pasted or attached artifacts show or describe the same behavior referenced within the issue. 
- The error behavior shown are from the same steps as described in the issue, matching behavior from the wrong steps don't count as correct.

## Honesty
Where it lives:
- Eval: the results described within the Candidate claim comment do not contradict the results shown within the Candidate repro report or its artifacts, whether or not the issue was reproduceable, as well as statements compared to evidence regarding the root causes of the issue.
- Live: the results described in the draft do not contradict the artifacts included with the draft, whether or not the issue was reproduceable, as well as statements compared to evidence regarding root causes of the issue.

What good looks like:
- Statements similar to "I reproduced this issue by" are only honest when the artifacts included demonstrate that the issue was reproduced in that same manner.
- Statements similar to "I could not reproduce this issue" are only honest when the artifacts show the attempt was made, including the relevant environment and steps, with descriptions of where the behavior was different.
- Statements similar to "The issue was caused by" are only honest when the steps and artifacts support it
- No statements that make unfounded gaurentees (e.g. done in two days max! and O(n) or better!)

## Comms
Where it lives:
- Eval: The Candidate claim comment and the Candidate repro report compared with the contribution policy and AI usage policy in the Repo facts.
- Live: the draft comments comapred with the CONTRIBUTING.md and AI.md files in the repository 

What good looks like:
- Comment claim, reports, or draft reports match policies listed in the contributing and ai policies for the repository, including all requirements with the correct formatting if specified; Inlcuding, but not limited to the claim comments or reports with all required disclosure, such as those specified statements regarding disclosures AI usage.
- If there are no mentioned policies regarding a topic, that policy is not required to be adhered to (e.g. if the repository does not require a disclosure then a disclosure does not need to be made).

