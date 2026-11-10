# Diagram selection

Use one diagram for one question. Keep labels concrete and readable at normal Markdown width.

| Need to explain | Use | Focus |
| --- | --- | --- |
| Components, boundaries, control or data paths | Flowchart | Direction, ownership, interfaces |
| Calls and responses over time | Sequence | Actors, ordering, success/failure branches |
| Lifecycle and transitions | State | States, guards, terminal states |
| Domain or code relationships | Class | Ownership, inheritance, key operations only |
| Persistent data relationships | ER | Cardinality and entity names |
| Quantitative comparison or trend | XY chart | Units, scale, source period |

For architecture documents, usually begin with a flowchart. For an implementation document, pair the structural flowchart with a sequence or state diagram only when lifecycle or ordering is a separate question.

Avoid diagrams that restate a short list. Do not mix deployment topology, request flow, and schema detail into one chart.

## Compatibility record

Create `docs/diagrams/ISSUES.md` on the first native-Mermaid exception:

```markdown
# Diagram compatibility exceptions

| Date | Document and heading | Mermaid type | Reason | Status |
| --- | --- | --- | --- | --- |
| 2026-07-20 | `docs/plan.md` — `## Timeline` | gantt | Not supported by beautiful-mermaid | Native Mermaid retained |
```
