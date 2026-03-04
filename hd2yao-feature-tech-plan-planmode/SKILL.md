---
name: hd2yao-feature-tech-plan-planmode
description: Use when a feature discovery summary exists and a detailed implementation plan is needed in plan mode, including frontend design when UI is involved.
---

# HD2YAO Feature Tech Plan (Plan Mode)

## Overview

Convert discovery into an executable implementation plan.

**Announce at start:** "I'm using hd2yao-feature-tech-plan-planmode to build a detailed plan in plan mode."

## Process

1. Load `./<feature>.discovery.md` if available.
2. If missing, create a minimal assumptions section and continue.
3. Build a detailed plan with exact files, tests, and rollback path.
4. If frontend is involved, include dedicated frontend design sections.
5. Save plan in the current repository root as versioned markdown.

## Output

Save to: `./<feature>.plan.v1.md`

Required sections:

```markdown
# <Feature> Implementation Plan

## Goal

## Scope

## Architecture

## Backend Changes

## Frontend Design (required when UI is involved)
- Information architecture
- States and interactions
- Responsive behavior
- Accessibility
- Validation screenshot points

## Data and API Changes

## Task Breakdown

## Test Strategy

## Rollback Plan

## Risks and Mitigations
```

## Quality Gate

Do not hand off to implementation until:
- Tasks are independently executable.
- Tests are mapped to acceptance criteria.
- Rollback strategy is actionable.

## Handoff

Invoke `hd2yao-feature-plan-review-iteration` for review-driven version updates.
