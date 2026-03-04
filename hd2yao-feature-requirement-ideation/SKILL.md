---
name: hd2yao-feature-requirement-ideation
description: Use when starting a new feature and requirements are ambiguous; clarifies goals, scope, constraints, and acceptance criteria before writing plans or code.
---

# HD2YAO Feature Requirement Ideation

## Overview

Clarify what should be built before planning or implementation.

**Announce at start:** "I'm using hd2yao-feature-requirement-ideation to clarify feature requirements."

<HARD-GATE>
Do not finish this skill with chat-only content. You MUST write the discovery output to disk and verify the file exists before handoff.
</HARD-GATE>

## Process

1. Collect context from user request and current project state.
2. Clarify goals, scope boundaries, constraints, and success criteria.
3. Identify assumptions and open questions explicitly.
4. Write the discovery document to disk in the current repository root.
5. Verify persistence with `test -f ./<feature>.discovery.md`.
6. Report the saved file path, then ask for confirmation before moving to technical planning.

## Output

Save to: `./<feature>.discovery.md`

Use this structure:

```markdown
# <Feature> Discovery

## Problem Statement

## Goals

## Non-Goals

## Target Users and Scenarios

## Constraints
- Technical
- Product
- Timeline

## Assumptions

## Acceptance Criteria

## Open Questions
```

## Mandatory Persistence Rule

- Writing to disk is required, not optional.
- Chat-only summaries do not satisfy this skill's output requirement.
- If file write or verification fails, report the blocker and stop. Do not hand off.

## Quality Gate

Do not hand off to planning until:
- Scope and non-goals are explicit.
- Acceptance criteria are testable.
- Open questions are either resolved or tracked.
- `./<feature>.discovery.md` exists on disk and its path has been reported.

## Handoff

When approved, invoke `hd2yao-feature-tech-plan-planmode`.
