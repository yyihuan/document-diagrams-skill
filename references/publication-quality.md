# Shared document diagrams

Prefer useful diagrams throughout structure-heavy documents. One figure should answer one question: use separate topology and sequence figures when they explain different things. Label arrow meaning, ownership, failure paths and unknowns. Verify important relationships against source evidence; do not invent missing architecture.

## Source and accessibility

Preserve the paired `.mmd` and generated SVG workflow. The existing freshness checker verifies source digest and renderer metadata; it does not detect arbitrary edits to SVG content, establish factual accuracy or certify security.

Add meaningful Markdown alt text and nearby prose explaining the key relationships. Native Mermaid supports `accTitle` and `accDescr`; verify actual output before claiming that beautiful-mermaid implements those directives. Inspect labels, clipping, contrast and edge direction at ordinary reading width and on narrow screens. Syntax acceptance alone is insufficient.

Use local rendering for private diagrams. Do not paste private source into hosted editors. Prefer plain-text labels; review active links or HTML before embedding generated SVG. Mermaid's `securityLevel` belongs to that runtime and does not certify another renderer's output.

## Technology choices checked 2026-11-10

- [beautiful-mermaid](https://github.com/lukilabs/beautiful-mermaid/blob/main/README.md) supports six diagram families and SVG/ASCII output. Retain the existing pinned 1.1.2 renderer; newer releases need compatibility tests before adoption.
- [Native Mermaid accessibility](https://mermaid.js.org/config/accessibility.html) provides title and description semantics. Keep prose alternatives even when these work.
- [Architecture beta](https://mermaid.ai/open-source/syntax/architecture.html) offers dedicated architecture syntax. It is outside the current wrapper's supported families. Retain the existing native-fence exception rather than introducing a second renderer automatically; if the destination cannot display it, supply a prose equivalent and report the limitation.
- [Mermaid home](https://mermaid.js.org/) currently promotes a DOM-free, plugin-based v13 proof of concept. Its performance claims are upstream claims, not measurements of this skill. Evaluate separately; do not migrate production documentation to an alpha merely because it is new.
- [Native Mermaid configuration](https://mermaid.js.org/config/schema-docs/config.html) includes layout and security controls. Verify the destination's actual version before using new grammar or options.

For measured data, use a plotting tool when scale, interpolation, error bars or publication fidelity matter. Smoothed illustrative curves must not imply measured intermediate values. None of these sources establishes automatic correctness of AI-generated diagrams or novelty of this workflow.
