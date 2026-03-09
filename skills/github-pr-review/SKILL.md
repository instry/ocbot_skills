---
name: github-pr-review
description: Summarizes pull request changes and posts a structured review comment on GitHub. Use this when the user wants an automated code review covering file-level diffs, potential issues, and improvement suggestions for a specific PR.
triggerPhrases:
  - review this PR
  - summarize pull request
  - code review github
  - github PR审查
  - 审查这个PR
startUrl: "https://github.com"
urlPattern: "github.com"
categories:
  - developer-tools
  - github
parameters:
  - name: review_style
    type: select
    description: "Level of detail in the review comment — concise gives a brief summary, detailed includes line-by-line analysis"
    required: false
    default: "concise"
    options: ["concise", "detailed"]
preconditions:
  - type: url_contains
    value: "github.com/"
    description: "Browser must be on a GitHub pull request page"
  - type: url_contains
    value: "/pull/"
    description: "URL must contain /pull/ indicating a pull request page"
---

# GitHub PR Review Helper

## Workflow
1. Open the "Files changed" tab on the current pull request page.
2. Read through each changed file, collecting: filename, change type (added/modified/deleted), lines added/removed, and notable code patterns.
3. Identify potential issues: bugs, security concerns, style violations, missing error handling.
4. Compose a structured review comment based on {{review_style}}.
5. Click the "Review changes" button, paste the review into the comment box, select "Comment", and submit.

## Preconditions
- Browser must be on a GitHub pull request page (URL contains `/pull/`).
- User must be logged into GitHub with write access to the repository (to post comments).

## Success Criteria
- A review comment is successfully posted on the PR with a structured summary.
- The comment includes: overview of changes, list of files modified, and any flagged issues.

## Notes
- For "concise" style, the review is kept under 200 words focusing on key changes and critical issues.
- For "detailed" style, each file gets its own section with line-level observations.
- The skill does not approve or request changes — it only posts informational comments.
