---
name: hd2yao-feature-implementation-delivery
description: Use when an approved feature plan is ready for implementation with parallel task execution, code review checkpoints, browser validation evidence, and final testing.
---

# HD2YAO Feature Implementation Delivery

## Overview

Execute an approved plan with controlled parallelism, review checkpoints, evidence collection, and final verification.

**Announce at start:** "I'm using hd2yao-feature-implementation-delivery to execute and deliver this feature."

## Process

1. Load final approved plan: `./<feature>.plan.vN.md`.
2. Create or switch to an isolated branch/worktree if needed.
3. Split tasks into independent units for optional parallel execution.
4. Implement with small, rollback-friendly commits.
5. Run review checkpoints during implementation.
6. For browser workflows, run automation and capture screenshots.
7. Run fast relevant checks first, then full relevant tests.
8. Commit and push all required changes to the feature branch.
9. Open or update a PR to target branch and include implementation/testing evidence.
10. Wait for required CI checks to finish and pass.
11. Address review comments or CI failures with additional small commits.
12. Merge PR only after required checks and approvals pass.
13. Produce implementation report with commit, PR, CI, and merge status.

## Required Practices

- Commit in small independent units.
- Do not bundle unrelated changes.
- Run code review checkpoints for risky or major chunks.
- Capture browser evidence when UI behavior is part of acceptance.
- Do not declare completion without verification output.
- Do not merge before required CI checks are green.
- If repository has PR protection rules, follow them strictly.
- If PR/CI workflow is unavailable, report blocker and get explicit user approval before direct merge.

## Output

Save to: `./<feature>.impl-report.md`

Include:

```markdown
# <Feature> Implementation Report

## Changes Delivered

## Commit Units

## Review Findings and Fixes

## Browser Validation and Screenshots

## Test Commands and Results

## Residual Risks

## PR and CI
- PR link and status
- Required CI checks and results

## Merge
- Merge method
- Final merged commit SHA
- Target branch
```

## Quality Gate

Feature is complete only when:
- Required tests pass.
- Acceptance criteria are verified.
- Evidence (logs/screenshots) is available when needed.
- Rollback path remains clear.
- Changes are committed and pushed to the branch.
- PR is created/updated and review requirements are satisfied.
- Required CI checks are green.
- PR is merged to target branch (or explicit approved exception is documented).
