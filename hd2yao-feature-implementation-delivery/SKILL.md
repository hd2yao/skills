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
8. Produce implementation report and readiness status.

## Required Practices

- Commit in small independent units.
- Do not bundle unrelated changes.
- Run code review checkpoints for risky or major chunks.
- Capture browser evidence when UI behavior is part of acceptance.
- Do not declare completion without verification output.

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
```

## Quality Gate

Feature is complete only when:
- Required tests pass.
- Acceptance criteria are verified.
- Evidence (logs/screenshots) is available when needed.
- Rollback path remains clear.
