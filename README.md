# document-diagrams

Reviewable Mermaid diagrams for Markdown documents, with paired source/SVG files and source freshness checks.

## Use

Install Node.js and npm, then run from this repository:

```sh
npm ci
node scripts/diagram.mjs render examples/request-lifecycle.mmd
node scripts/diagram.mjs check examples/request-lifecycle.mmd
```

Set `DIAGRAM_SKILL_ROOT` to this repository’s absolute path when following SKILL.md commands. The renderer is pinned to beautiful-mermaid 1.1.2.

![Request authorization and outcome recording](examples/request-lifecycle.svg)

The example branches on authorization and records both execution and rejection outcomes.

## Versions and provenance

- `v0.1.0`: snapshot of the existing local skill before this refresh. Personal absolute paths were normalized and caches excluded; original rules were retained. This tag was created during publication, not at the historical date the skill was first written.
- `v0.2.0`: the refreshed skill, with supporting references and examples.

## Verification and limits

Skill frontmatter checks passed. Diagram rendering and source freshness were checked, including rejection after source changes and recovery after rendering. References and sample HTML image paths were checked. Tests used the existing pinned local renderer installation. Clean-machine npm installation, browser visual review, screen-reader behavior and external Gemini execution have not been verified. The freshness check verifies source digest and renderer metadata, not arbitrary SVG edits or factual correctness.

No license is granted beyond applicable default rights for original material at this stage. External software and linked sources retain their own licenses; dependencies are not vendored.
