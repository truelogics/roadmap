---
doc: NOW
audience: [human, agent]
status: living
owner: product
last_reviewed: 2026-08-08
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

Active work — this sprint or week. Keep to **1–3 items**.

- [ ] Write `ai-review`'s documentation (vision, architecture, kernel
      requirements) — no code yet, deliberately. Its gap list becomes AI
      Memory's next real milestones instead of speculative ones. AI
      Memory's kernel itself (indexing, hybrid search, graph, context
      assembly) is implemented and paused — external integrations
      (plugins, HTTP API) are deferred until AI Review proves what's
      actually needed.
