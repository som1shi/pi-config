---
name: github-issues
description: Triage, draft, or revise GitHub issues for bugs, feature requests, and investigations. Use to establish issue scope, ownership, evidence, duplicates, and observable completion criteria; not for routine issue lookup or PR review comments.
---

# GitHub Issue Authoring

Turn the requested outcome and available evidence into a useful issue. Use [github](../github/SKILL.md) for `gh` operations and shared mutation rules; this skill owns issue content and triage, not permission to publish.

## Establish the issue

1. Read the request and relevant current source, existing issue, or planning material. Reuse decisions already supplied; ask only for unresolved material choices.
2. Identify the problem, requested capability, or investigation question, its scope, and the intended outcome. A feature request does not need measured harm; an investigation does not need a proven root cause.
3. Establish the affected owner and impact only as far as evidence supports them. Keep unknown causes, frequency, and impact explicit rather than inventing certainty.
4. Search issue titles and bodies in the target repository and other plausible owner repositories identified by evidence. Check whether the outcome is already covered or resolved.
5. Choose the right artifact: a new issue, an update to an existing issue, an evidence comment, a title correction, or no action. Explain a duplicate, already-fixed, or wrong-owner disposition and its better destination.
6. Define observable completion criteria with the user’s intended scope. For an investigation, specify the question to answer and useful evidence or decision to deliver, not an assumed fix.

Research only sources that can change the scope, ownership, or evidence. Do not turn drafting into an unrelated audit. If a needed source is unavailable, state that limit; do not claim a complete duplicate or ownership check.

## Keep claims accurate

- Link factual claims to current evidence and distinguish it from proposals, partial fixes, historical work, and undeployed changes.
- Do not equate log rows, wrapper errors, requests, incidents, or affected users without evidence connecting them. Do not generalize one event to an entire error group.
- Include related work only after reading enough to establish its relevance. Explain its relationship or limitation, rather than collecting thematic links.
- Keep credentials, secrets, and unnecessary personal data out of the issue.

## Draft the content

Follow the repository’s title conventions. Use short sections only when they help:

- **Context:** what is happening or requested, why it matters, and material unknowns.
- **Evidence:** direct observations or links and what they establish.
- **Outcome:** the agreed change, capability, or investigation goal.
- **Done when:** observable completion criteria within that scope.
- **Related work:** only material overlap, ownership, dependencies, or useful precedents.

Include an implementation direction when supplied or agreed, but do not invent architecture, thresholds, schemas, rollout steps, defenses, or test requirements. Do not add an empty implementation placeholder. A draft should be actionable without prescribing an unrequested design.

Present the target repository, exact proposed title and body, and any separately requested metadata changes. Use [review](../review/SKILL.md) for a nontrivial review; its existing policy owns review depth. Drafting ends with the draft unless publication was separately requested and approved.

## Revise an existing issue

Read its current title, body, relevant comments, state, and fields affected by the requested change before proposing an update. Preserve strong existing wording and structure instead of rewriting to fit a template. Prefer a small evidence comment or title-only correction when that meets the request.

Do not silently change labels, assignees, state, projects, parent/subissue relationships, or planning documents. Keep unapproved fields unchanged.

## Apply an authorized change

Follow `github` and active external-action policy: state the exact tool, target, action, fields, and expected persistent effect, then obtain the required approval. A draft does not authorize creation, commenting, metadata changes, or adjacent updates.

Before an approved creation, refresh the bounded duplicate check. Before an approved update, re-read the relevant target state and compare the content and fields on which the proposal depends. If those changed, stop and reassess rather than overwrite a concurrent edit. This is an observational check, not an atomic lock.

Use a body file for multiline content. Apply only the approved change, then read back the canonical URL, resulting content, state, and affected metadata. Stop on stale preconditions, partial failure, timeout, or an ambiguous result; inspect the resulting state before considering any retry. Never retry a mutation blindly.
