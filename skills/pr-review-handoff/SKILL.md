---
name: pr-review-handoff
description: Draft a concise author-to-human PR review request when the user asks to hand off their PR for human review. Not for agent/context handoffs, ordinary PR preparation, reviewing another PR, or responding to feedback.
---

# PR Review Handoff

Prepare the requested human-review message, not another review workflow. Use [github](../github/SKILL.md) for current PR information, claim-dependent evidence freshness, and shared mutation rules. Generic agent or context handoff remains with [delegation](../delegation/SKILL.md).

Reuse applicable evidence already current for the PR. Do not start a new full review or live test merely to draft a handoff. When evidence is missing or stale, state the limitation rather than claim readiness.

## Draft the request

Include only the useful details:

- PR link.
- One-sentence purpose.
- The most useful review focus and any requested depth, in ordinary language.
- Evidence status: what was checked, what that proves, and any material unverified behavior.

Distinguish static checks, CI, and live evidence. Use [behavioral-proof](../behavioral-proof/SKILL.md) to interpret their scope; an appropriate non-live proof is not a missing live-test defect.

For example: “Please review <PR link>: <purpose>. Focus on <area or question>. Verified: <evidence>. Not checked: <material boundary, if any>.”

Do not quiz the author, repeat readthrough prompts, impose review-level labels, or tell the reviewer to approve. Report missing evidence once and continue with the requested draft.

Drafting does not post a message, request reviewers, change the PR, or dispatch agents. Any external action requires the separate exact authorization defined by `github` and active policy.
