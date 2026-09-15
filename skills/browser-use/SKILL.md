---
name: browser-use
description: Automates browser interactions for web testing, form filling, screenshots, and data extraction. Use when the user needs to navigate websites, interact with web pages, fill forms, take screenshots, or extract information from web pages.
allowed-tools: Bash(browser-use:*)
---

# Browser Automation with browser-use CLI

Use plain HTTP fetching first for public information. Use the browser when interaction or rendered UI evidence is needed.

## Prerequisites and isolation

- Require an installed `browser-use` CLI and an explicit HTTP CDP endpoint. Default to a task-owned isolated browser. If either prerequisite is missing, report it and stop.
- The CLI can attach to personal Chrome by default. Never use that implicit default or copy profiles. Use an existing personal browser only when the task requires its state and the user explicitly approves the specific browser/account.
- Choose a unique `BU_NAME` for the task. Set that same name and the task's `BU_CDP_URL` explicitly on **every call**, including diagnostics. Never reuse an unknown named daemon or drop the endpoint to recover from a failure.
- Installation, personal-account authentication, cloud provisioning, and browser setup are outside this workflow. Do not try a fallback chain.

Replace the placeholders with the task's verified name and isolated endpoint:

```bash
BU_NAME='<unique-task>' BU_CDP_URL='http://<task-owned-host>:<port>' browser-use --help
BU_NAME='<unique-task>' BU_CDP_URL='http://<task-owned-host>:<port>' browser-use --doctor
```

## Workflow

The CLI executes Python with browser helpers pre-imported. Its daemon preserves the attached tab between calls.

1. Open the task's first page with `new_tab(url)`, then `wait_for_load()` and inspect `page_info()`.
2. Reuse the task's tab. Check `current_tab()` and `list_tabs()` before opening another; use `switch_tab()` for a matching task-owned tab. Do not close tabs you did not create.
3. Inspect with `js(expr)` or targeted `cdp(method, **kwargs)` calls. For clicks, inspect the accessibility tree and element box, then use `click_at_xy(x, y)` with viewport CSS coordinates. Verify the resulting state before continuing.
4. For local development login, use the app's documented test-auth flow. Stop for real passwords, MFA, consent, or account choices; do not borrow personal browser state.
5. Capture UI evidence with `capture_screenshot(path, max_dim=1800)`. Create the parent directory under `.scratch/` with normal file tools first, then inspect the saved image. Do not use resized image coordinates directly for clicks; measure the element in CSS coordinates.

Example for an already-running local app, after creating `.scratch/ui-screenshots/`:

```bash
BU_NAME='<unique-task>' BU_CDP_URL='http://<task-owned-host>:<port>' browser-use <<'PY'
new_tab("http://127.0.0.1:<app-port>")
wait_for_load()
print(page_info())
print(js("document.title"))
capture_screenshot(".scratch/ui-screenshots/page.png", max_dim=1800)
PY
```

On failure, inspect the error and run diagnostics with the same name and endpoint. If browser ownership or authorization cannot be verified, stop and report the blocker.

## References

- [Current CLI documentation](https://docs.browser-use.com/open-source/browser-use-cli.md)
- [Upstream skill and helpers](https://raw.githubusercontent.com/browser-use/browser-use/main/skills/browser-use/SKILL.md)
- [Screenshot behavior and coordinates](https://raw.githubusercontent.com/browser-use/browser-harness/main/interaction-skills/screenshots.md)
