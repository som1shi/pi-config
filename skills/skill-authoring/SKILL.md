---
name: skill-authoring
description: Create, review, or substantially revise local Pi skills. Use for activation descriptions, package structure, progressive-disclosure references, helper justification, and structural validation. Not for ordinary application code/docs or Pi settings and package installation.
---

# Skill Authoring

Build the smallest skill package that a current task can use, with one clear owner.

## Establish ownership

- Identify the current consumer and normal entry point. Inspect existing skills before adding another owner.
- Put new guidance in an existing owner when it fits cleanly. Do not copy shared approval, review, or tool policies into every skill.
- This skill owns content, activation, and package structure. `manager-workflow` owns material implementation stages and approval; `review` owns substantive review. Follow the active configuration policy for placement, precedence, settings, and package changes.
- A request to review a skill does not authorize editing it.

## Define activation

Read [the activation contract](references/activation-contract.md). Describe the capability and natural-language trigger, then check paraphrases, near misses, and exclusions. Keep detailed procedure out of the description because it is always visible in the catalog.

## Keep the package focused

Keep the normal workflow in `SKILL.md`. Move useful optional detail into directly linked, one-level references. Resolve supporting paths from the skill directory, not the current repository.

Add a helper only for a reached, repeated deterministic operation that reduces ambiguity or manual error. State its inputs, output, failures, and effects; use `writing-tests` for owned helper behavior. Do not add a parser, validator, reference tree, or compatibility layer without a concrete need.

## Validate and report

Follow [structural validation](references/structural-validation.md): use the installed Pi loader for metadata and discovery, inspect reached references and helpers separately, and verify the relevant catalog exposure. Report the exact discovery scope and any warnings or unavailable checks.

Review representative activation cases as design evidence. Discovery and static case review do not prove model selection or task success. Comparative activation or outcome evaluation is a separate authorized task governed by the active session's approval authority; do not run it or persist evaluation cases automatically.

Reviewer and validator results are evidence, not permission to expand the task.
