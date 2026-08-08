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

The objective is to validate AI Review as the first production-quality
consumer of AI Memory.

Current priorities:

1. Improve review quality.
2. Improve evidence quality.
3. Expand benchmark coverage.
4. Dogfood AI Review daily.
5. Reach the first public alpha.

Future integrations (Claude Code, MCP, GitHub, VS Code, Cursor, CI)
remain out of scope until AI Review is proven through benchmarks and
real-world usage.

## Sprint 7 — Workspaces (in progress)

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
- **Category B proven end to end:** a review of `ai-review` against a
  workspace holding `ai-review` and `engineering` retrieves
  `rules/no-silent-fallback.md` — the rule governing the file under
  review — from the other repository. `Rules: 0` → `Rules: 3`.

**Next:** the Workspace Model RFC, for what genuinely remains — a
first-class `workspaces` table and named workspaces, repository
priority, rules-only repositories, and `applies_to`-scoped rule lookup
(`KERNEL_REQUIREMENTS.md` #6, now evidence-backed: the first rule ever
retrieved was a TypeScript rule for a Go diff).

Then resume Sprint 6: review quality, benchmarks, dogfooding.

---

Active work — this sprint or week. Keep to **1–3 items**.

- [ ] Write `ai-review`'s documentation (vision, architecture, kernel
      requirements) — no code yet, deliberately. Its gap list becomes AI
      Memory's next real milestones instead of speculative ones. AI
      Memory's kernel itself (indexing, hybrid search, graph, context
      assembly) is implemented and paused — external integrations
      (plugins, HTTP API) are deferred until AI Review proves what's
      actually needed.
