# Rubric: is this a good first issue?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Repository-maintained-recent | Recent default-branch commits | the last 5 default-branch commit dates are within the last 90 days |  required |
| Repository-active-releases | Release recency | the latest release is within the last 6 months or has no releases yet | required |
| Repository-active-open | Archived flag | the repository is not marked as archived and read only | required |
| Repository-allows-AI | Contribution policy | the contribution policy does not explicitly disallow AI use or its assistance | required |
| Issue-scope-clear | Issue body and thread text | the issue's specified problem is clearly defined and is not heavily debated | required |
| Issue-scope-design | Issue header and body text | the issue is not a product decision or company design choice (e.g. add a logo, create a slogan, or improve look) | required |
| Issue-scope-support-request | Issue header and body text | the issue is not a support request (e.g. "how do I make this work?") | required |
| Issue-scope-history | Linked PRs | the issue does not have more than 1 abandonded attempts | required |
| Issue-available-not-assigned | Assignee | the issue is not already assigned to someone else | required |
| Issue-available-not-worked | Linked PRs | there are no linked open PRs on the issue or mentioned in the comments | required |
| Issue-available-not-comment-claimed | Claim comments | the maintainer has not given the issue as a reply to someone requesting it in the comments | preferred |
| Issue-reproduceable-steps | Issue description text | the information in the issue text contains steps for reproducing the issue | preferred |

## Verdict rule

Verdict is accepted if every required check passes; 
A failure in a preferred check does not affect the verdict.
Unclear for a required check counts as a fail; unclear for a preffered check counts as a pass.

