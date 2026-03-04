---
name: hd2yao-feature-plan-review-iteration
description: Use when a feature plan needs review feedback incorporated through versioned document updates until blocking comments are resolved.
---

# HD2YAO Feature Plan Review Iteration

## Overview

Iterate plan documents based on review feedback with strict traceability.

**Announce at start:** "I'm using hd2yao-feature-plan-review-iteration to process review feedback and iterate the plan."

<HARD-GATE>
Do not finish this skill with chat-only feedback. You MUST write the next plan version to disk and verify it exists before handoff.
</HARD-GATE>

## Process

1. Locate the latest plan file: `./<feature>.plan.vN.md` (or user-provided plan path).
2. Set current review round index `N` and create review directory beside the plan file: `./<plan-dir>/reviews/`.
3. Generate `./<plan-dir>/reviews/round-0N.claude-review-request.md` using the template in this skill.
4. Ask user to send only that request file to Claude (no extra explanation required).
5. Wait for Claude output file: `./<plan-dir>/reviews/round-0N.claude.md`.
6. If Claude output file is missing, stop and ask user to provide it before continuing.
7. Classify Claude findings as Blocking, Important, or Minor.
8. Update the plan and write next version: `./<plan-dir>/<feature>.plan.vN+1.md`.
9. Write resolution mapping file: `./<plan-dir>/reviews/round-0N.codex-resolution.md`.
10. Verify persistence for all round artifacts and next plan version.
11. Report saved paths and repeat until no blocking comments remain.

## Output

Primary output: `./<plan-dir>/<feature>.plan.vN+1.md`

Round artifacts (required):
- `./<plan-dir>/reviews/round-0N.claude-review-request.md`
- `./<plan-dir>/reviews/round-0N.claude.md`
- `./<plan-dir>/reviews/round-0N.codex-resolution.md`

Include this section:

```markdown
## Review Log

| ID | Severity | Comment | Decision | Notes | Status |
|----|----------|---------|----------|-------|--------|
```

## Claude Review Request Template

The generated `round-0N.claude-review-request.md` MUST be complete and directly usable by Claude:

```markdown
# Claude Plan Review Request (Round 0N)

You are reviewing this plan file:
- `<PLAN_FILE_PATH>`

Your task:
1. Read the entire plan.
2. Review for correctness, completeness, feasibility, rollback safety, and testability.
3. Output only concrete findings with severity.
4. Do not rewrite the whole plan.

Severity rules:
- Blocking: prevents safe implementation or likely causes incorrect behavior.
- Important: should be fixed before implementation but not immediately catastrophic.
- Minor: clarity/style improvements.

Output format (use exactly):

## Findings
| ID | Severity | Section | Issue | Suggested Change |
|----|----------|---------|-------|------------------|

## Summary
- Blocking count:
- Important count:
- Minor count:
- Verdict: BLOCKED or READY_FOR_NEXT_ROUND

Rules:
- Each finding must include a specific suggested change.
- Keep IDs stable in this round (e.g., `C-R0N-001`).
- No vague comments.
```

## Mandatory Persistence Rule

- Every review iteration must create the request file, Claude output file, Codex resolution file, and next plan version on disk.
- Chat-only review summaries do not satisfy this skill's output requirement.
- If file write or verification fails, report the blocker and stop. Do not hand off.

## Quality Gate

Implementation can start only when:
- Latest Claude review file exists on disk.
- Blocking comments count is 0.
- Important comments are resolved or explicitly deferred.
- Decisions are documented in the review log.
- The latest `./<plan-dir>/<feature>.plan.vN+1.md` file exists on disk and its path has been reported.
- Round artifacts are complete under `./<plan-dir>/reviews/`.

## Single-Use Mode

If user asks for one pass only, run one iteration and stop after writing all round artifacts and next plan version.

## Handoff

When approved, invoke `hd2yao-feature-implementation-delivery`.
