---
doc: NOW
audience: [human, agent]
status: living
owner: product
last_reviewed: 2026-08-09
---

# Now

## Current Focus

The current objective is **not** to build more features.

The objective is to validate Engineering Review as the first production-quality
consumer of Engineering Kernel.

Current priorities:

1. Improve review quality.
2. Improve evidence quality.
3. Expand benchmark coverage.
4. Dogfood Engineering Review daily.
5. Reach the first public alpha.

Future integrations (Claude Code, MCP, GitHub, VS Code, Cursor, CI)
remain out of scope until Engineering Review is proven through benchmarks and
real-world usage.

## Sprint 7 — Workspaces (complete)

**Goal:** enable one Engineering OS workspace to contain multiple
repositories, so a repository-specific review is grounded in shared
engineering knowledge.

**Motivation, as it actually turned out.** This sprint was opened on the
belief that the kernel could not hold two repositories in one workspace.
It always could, from Go. Testing each cause in isolation found three
different ones: `engineering/` contained no indexable rules, its
`rules/README.md` classified as a readme rather than a rule, and
multi-repository workspaces had no CLI surface, so nobody built one.

**Done:**

- `eng workspace create/list/attach/detach`; `eng index` now indexes
  every attached repository
- Seven real Go engineering rules written, and the three existing YAML
  rules converted to an indexable format
- Document classification: directory outranks file name
- `FileContext`/`SearchResult` carry `Repository`, so a path is
  attributable when two repositories share it
- `.eng.yaml` gains `review.workspace`
- **Category B proven end to end:** a review of `engineering-review` against a
  workspace holding `engineering-review` and `engineering` retrieves
  `rules/no-silent-fallback.md` — the rule governing the file under
  review — from the other repository. `Rules: 0` → `Rules: 3`.

## Sprint 8 — Engineering MCP (complete)

`engineering-mcp` ships: the second consumer of Engineering Kernel, exposing
proven capabilities over the Model Context Protocol. Three tools —
`search_memory`, `get_context`, `find_engineering_rules` — each already a
validated capability inside a real consumer (KERNEL_POLICY Rule #6).

Two of the five proposed tools were rejected by that rule and are
documented rather than built: `collect_evidence` (verification lives
inside Engineering Review's Validator, not the kernel) and
`get_architecture_context` (the public surface collapses architecture
with four other document classes, so the name would overclaim).

Named for the transport, not "server": MCP today, HTTP or gRPC later
over the same adapters.

**Two unrelated consumers now build on the same kernel.** That was the
bar for calling this a platform rather than an application.

---

## Sprint 9 — Evidence Capability (complete)

Evidence verification, excerpt normalization and confidence scoring
promoted from Engineering Review's Validator into `pkg/memory` (engineering-kernel
RFC-0006), requested independently by two consumers. Engineering Review's
duplicate is deleted, not wrapped; `engineering-mcp` exposes
`verify_evidence`. Four transport-independent capabilities now exist.

The first platform measurement also ran — Claude Code with and without
engineering-mcp, which needs no Anthropic credit — and **found no
difference**. Seven correctly-scoped rules came back; none governed the
defect. Recorded in `engineering-review/docs/reports/REVIEW_QUALITY_LOG.md`.

## Sprint 10 — Decision Support Experiment (design complete, not built)

The Sprint 9 result disproved a narrow hypothesis: *scoped rules plus
lexical ranking are sufficient*. It did not show the platform is
unhelpful.

[`engineering/DECISION_SUPPORT.md`](https://github.com/truelogics/engineering/blob/main/DECISION_SUPPORT.md)
places the boundary before any code: the platform answers questions
about what is written down; reasoning answers questions about what is
happening. Prioritization splits across it — the *signals* are platform,
the *policy* weighing them is consumer.

**Next, and only this:** run the three-arm experiment (no context /
all scoped rules / prioritized rules) with prioritization implemented
**inside a consumer**, since Rule #6 forbids inventing it at the
transport. Falsifiable prediction stated in the document.

Not building the layer until that answers yes.

---

**Deferred from Sprint 7:** the Workspace Model RFC, for what genuinely remains — a
first-class `workspaces` table and named workspaces, repository
priority, rules-only repositories, and `applies_to`-scoped rule lookup
(`KERNEL_REQUIREMENTS.md` #6, now evidence-backed: the first rule ever
retrieved was a TypeScript rule for a Go diff).

Then resume Sprint 6: review quality, benchmarks, dogfooding.

---

Active work — this sprint or week. Keep to **1–3 items**.

- [ ] Write `engineering-review`'s documentation (vision, architecture, kernel
      requirements) — no code yet, deliberately. Its gap list becomes AI
      Memory's next real milestones instead of speculative ones. AI
      Memory's kernel itself (indexing, hybrid search, graph, context
      assembly) is implemented and paused — external integrations
      (plugins, HTTP API) are deferred until Engineering Review proves what's
      actually needed.
