# Agent working agreements

## Every change goes through a pull request

**Hard rule. No exception for size** — documentation-only and one-line
changes included. One fix or one feature, one branch, one PR.

Never commit to `main` directly, and never merge a branch into `main`
locally. `main` moves only when a PR is merged.

Opening the PR is where the work ends. Merging is the owner's decision,
not the author's — including when the author is an agent, and including
when the owner has said "push" or "ship it". Those mean *get it ready to
merge*.

A merge that skipped review is indistinguishable, afterwards, from one
that passed it. The PR is the only place a change is visible as a
proposal rather than as a fact.

## Before pushing

This repository holds documents, not code. Check that links resolve and
that front matter is present and correct
(`engineering:rules/doc-front-matter.md`) — it is what decides how
Engineering OS classifies a document, and a missing `doc:` makes a file
retrievable only as a keyword hit.

## The full agreements

Versioned and indexed in the [`engineering`](https://github.com/truelogics/engineering)
rulebook, which is the source of truth for this file:

- `rules/every-change-through-a-pr.md`
- `rules/pr-single-purpose.md` — what belongs in one PR
- `rules/doc-front-matter.md`
