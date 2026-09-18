# Activation contract

A skill description is a routing contract, not a summary of its entire package. Pi exposes discovered names, descriptions, and paths in the model-visible catalog; the full instructions load when selected or explicitly invoked.

## Define the boundary

Identify:
- the behavior this skill owns and its current consumer;
- direct natural-language triggers and common paraphrases;
- adjacent requests that belong to another owner;
- requests that must not activate this skill.

For example, changing a skill's frontmatter and references belongs to `skill-authoring`; changing Pi settings or installing a package does not. Ordinary application code and documentation are negative cases.

## Write the description

State both capability and trigger:

```yaml
description: Extract text and tables from PDF files. Use when reading, converting, or inspecting PDF documents.
```

Prefer concrete user language. Add an exclusion or handoff only when it prevents a plausible routing collision. Avoid vague claims, feature inventories, universal activation, setup instructions, and references to unavailable tools or owners.

## Review the cases

Use a small set that can expose a routing mistake:
- a direct request;
- a synonym or paraphrase;
- a near miss routed to its actual owner;
- an unrelated negative control;
- a fresh-context case without prior conversational hints.

These cases guide description review; they are not a mandatory model benchmark. Native discovery verifies catalog availability, not whether a model chooses the skill. Comparative activation evaluation remains a separate authorized task under active-session authority.
