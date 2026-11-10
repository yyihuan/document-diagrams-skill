---
name: document-diagrams
description: Create, update, or review architecture, design, implementation, workflow, data-model, and other structure-heavy Markdown documentation with reviewable Mermaid diagrams. Use when a document needs an embedded diagram, Mermaid source management, beautiful-mermaid SVG rendering, or diagram freshness checks.
---

# Document diagrams

Make architecture, design, implementation, workflow, and data-model documents include at least one diagram that explains their structure or behavior.

## Source and layout

- Treat `*.mmd` as the only editable source. Render its same-name `*.svg`; never hand-edit generated SVG.
- Store project documentation diagrams in `<project>/docs/diagrams/`. Use stable semantic names such as `request-lifecycle.mmd`, not a Markdown filename.
- Keep supported diagrams out of Markdown fences. Embed the SVG; the same-name `.mmd` in the same directory is its source mapping:

  ```markdown
  ![Request lifecycle](./diagrams/request-lifecycle.svg)
  ```

- Use the project's source-control policy for both files. Do not add a manifest: the SVG records the source digest and renderer metadata.

## Render and verify

Set DIAGRAM_SKILL_ROOT to the absolute directory containing this SKILL.md. Install pinned dependencies with npm ci in that directory when absent; never silently upgrade. Use the bundled renderer after creating or editing a source:

```bash
node "$DIAGRAM_SKILL_ROOT/scripts/diagram.mjs" render docs/diagrams/request-lifecycle.mmd
node "$DIAGRAM_SKILL_ROOT/scripts/diagram.mjs" check docs/diagrams
node "$DIAGRAM_SKILL_ROOT/scripts/diagram.mjs" check docs/architecture.md
```

Use `render-all <directory>` and `check-all <directory>` for a diagram directory. Inspect the resulting SVG in the target Markdown renderer when visual layout matters.

## Diagram choice

Read [diagram-selection.md](references/diagram-selection.md) before choosing a diagram type. Prefer the smallest diagram that makes component relationships, sequence, state, or ownership clear.

Render with the built-in `github-light` theme. Keep node labels short, distinguish data/control paths, and split unrelated concerns into separate diagrams.

## Compatibility exceptions

beautiful-mermaid supports flowchart, state, sequence, class, ER, and XY charts. For an unsupported Mermaid type, keep one native Mermaid fence in the document; do not create a duplicate `.mmd` or SVG.

Record the exception in `docs/diagrams/ISSUES.md` with date, document and heading, diagram type, reason, and status. Also update the personal Obsidian compatibility ledger when that vault is available. Do not introduce a second renderer merely to avoid an exception.

## Failure handling

- If rendering fails, keep the `.mmd` source, report the parser or renderer error, and do not replace it with a hand-drawn SVG.
- If `check` reports an old or missing SVG, re-render before declaring the documentation complete.
- If a target project has an explicit stricter documentation policy, follow it while retaining the single-source and freshness guarantees above.

## Publication quality

Read [publication-quality.md](references/publication-quality.md) for accessible, evidence-backed diagrams and current renderer choices. Preserve the preference for useful diagrams across a document; cover distinct questions rather than filling a quota. Syntax success does not establish factual accuracy.
