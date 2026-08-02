---
doc: MILESTONES
audience: [human, agent]
status: living
owner: product
last_reviewed: 2026-08-02
---

# Milestones

Major goals and target dates — outcomes, not task lists.

| Milestone | Target | Outcome |
|-----------|--------|---------|
| Engineering Memory Kernel design | 2026-08-02 ✅ | RFC-0001, architecture, domain model, database schema, and CLI design shipped in `ai-memory/` |
| AI Memory kernel (Milestones 1-7) | 2026-08-02 ✅ | Indexing, incremental sync, relationship graph, hybrid search, context assembly, configurable ranking — all implemented and tested end-to-end in `ai-memory/` |
| AI Review documentation | _TBD_ | Vision, architecture, and kernel-requirements written in `ai-review/` before any code — the gap list becomes AI Memory's next milestones |
| AI Memory public API + Go SDK facade | _TBD_ | Blocking requirement from `ai-review/KERNEL_REQUIREMENTS.md` — nothing outside `ai-memory` can import it until this exists |
| AI Review v1 (first consumer) | _TBD_ | A real PR review powered by AI Memory's context — proves the kernel against actual usage instead of speculation |
| Engineering brain | _TBD_ | RFC/ADR/rules repo consumable by AI review |
