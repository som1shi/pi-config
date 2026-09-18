# Structural validation

Use Pi's installed loader rather than maintaining a second frontmatter parser. Structural checks establish package shape and discovery, not instruction quality or model behavior.

## Package and resources

A skill needs only `SKILL.md`. Add references, scripts, tests, or assets only when the actual workflow reaches them.

- Check frontmatter against the installed Pi version's `docs/skills.md`, including name/description limits and intended model visibility.
- Read linked references. Resolve package-relative paths from the containing document and confirm every reached helper or asset exists.
- Keep optional detail one reference level from `SKILL.md`; avoid discovery chains.
- Inspect helper dependencies, commands, inputs, outputs, and effects. Loading a skill does not validate or authorize executing its helpers.

## Native discovery without a model

Locate the installed Pi package from the actual `pi` executable or the project's package resolution. Verify its `package.json`, `docs/skills.md`, and current loader API; do not assume a personal installation path or resolve from an unrelated working directory.

The current API in `dist/core/skills.js` exposes `loadSkillsFromDir({ dir, source })`, returning `skills` and `diagnostics`, and `formatSkillsForPrompt(skills)`. After resolving both absolute paths and verifying those exports, this read-only check loads metadata and formats the catalog without starting a Pi session or calling a model:

```bash
pi_package_dir="/absolute/path/to/verified/pi-package"
skills_dir="/absolute/path/to/skills-under-review"
node --input-type=module - "$pi_package_dir" "$skills_dir" <<'JS'
import { resolve } from 'node:path';
import { pathToFileURL } from 'node:url';
const [packageDir, skillsDir] = process.argv.slice(2);
const { loadSkillsFromDir, formatSkillsForPrompt } = await import(
  pathToFileURL(resolve(packageDir, 'dist/core/skills.js')).href
);
const { skills, diagnostics } = loadSkillsFromDir({ dir: skillsDir, source: 'skill-review' });
console.log(JSON.stringify({
  skills: skills.map(({ name, filePath, disableModelInvocation }) => ({
    name, filePath, disableModelInvocation
  })),
  diagnostics,
  catalog: formatSkillsForPrompt(skills)
}, null, 2));
JS
```

Inspect diagnostics, resolved paths, expected names, collisions, and the formatted catalog. Confirm expected model-visible skills appear and `disable-model-invocation` skills remain excluded.

A directory check does not establish merged discovery or precedence across project, global, settings, and package sources. When that boundary changes, inspect the actual configured resource loader's resolved sources and diagnostics. Do not claim effective precedence from a single directory or invent a CLI discovery command. If that check is unavailable, name the unverified boundary.

## Evidence report

State the installed Pi version, inspected directory/configuration scope, discovered names, visibility, diagnostics, and separately checked resources. Distinguish warnings, failures, unavailable checks, and clean results. Native loading does not validate resource links, helper execution, model activation, or task outcomes.

Do not install dependencies, connect services, reload a running session, or run comparative model evaluation merely to validate metadata. Such actions remain subject to the active task and approval authority.
