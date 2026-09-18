---
name: notion-documents
description: Draft, revise, and format Notion documents. Use for turning notes into a Notion page or improving a page's structure and readability. Covers document content and existing embedded views, not database/workflow design or connection setup.
---

# Notion Documents

Create clear, audience-directed documents and preserve existing content outside the requested change.

## Choose the task boundary

Drafting can use supplied content without a Notion connection. If live page access is needed, inspect the available tool descriptions and the current [Notion enhanced-Markdown specification](https://developers.notion.com/guides/data-apis/enhanced-markdown) for the operation. Do not treat enhanced Markdown as ordinary Markdown or assume an editor feature is exposed by the tool.

If no suitable tool is available, report that boundary and provide a draft when useful. Do not install, connect, authenticate, or claim a page was updated as a fallback. Live page creation and edits remain external mutations governed by the active approval policy; a drafting request does not authorize them.

## Compose for the reader

- Establish the document's purpose, audience, and requested outcome from the supplied context. Ask only for unresolved material decisions.
- For working notes and internal designs, prefer a compact outline. Let headings carry shared context; use prose when it explains a relationship more clearly.
- Keep intended behavior, scope, and reader decisions in the main text. Put supporting investigation beside the relevant topic, with consequential qualifications still visible.
- Distinguish verified facts, proposals, and open questions. Express uncertainty locally rather than repeating disclaimers or converting guesses into requirements.
- Include source facts and links for their relevance to this reader, not to reproduce an investigation log. Add diagrams, code, or screenshots only when they explain something better.
- Choose sections from the content, not a fixed template. Remove duplicated introductions, empty sections, and repeated points.
- Follow the user's supplied style and active output conventions. Do not impose new punctuation, colors, icons, tables, or other formatting preferences.

## Edit an existing page

1. Read the current page and affected content, including relevant formatting and block structure. If only an excerpt is available, limit claims and proposed changes to that excerpt.
2. Preserve wording, hierarchy, formatting, embedded views, and surrounding content outside the requested change. Propose a broader reformat separately rather than silently applying it.
3. Prefer targeted edits that retain native blocks over replacing the whole page or flattening it into plain text. Use only structures supported by the actual tool and document format.
4. Before a live write, follow the active external-action policy for the exact tool, page, changes, and expected effects. Apply only the authorized change.
5. Fetch the page after the write and inspect the intended change and preservation of surrounding content. Report a partial or failed write accurately rather than claiming completion from the request alone.

Readback verifies returned content, not visual rendering, persistent collapsed state, tabs, or diagram preview behavior. Verify those separately when they matter to the task; otherwise leave them unclaimed. Existing embedded views can be document content, but creating databases or changing workflows requires a separately scoped task.

## Return the result

For a draft, provide the proposed content and any material unresolved question without claiming publication. For an authorized live edit, identify the page and change, report the readback result, and name any relevant unverified presentation behavior.
