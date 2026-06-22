# Skill spec · `canon-finder`

> `/canon-finder <domain-or-layer>` — find the 5–10 tried-and-true foundational
> resources a field treats as canon, with access flags, before the gates matter.

Wraps prompt [`02-canon-finder`](../prompts/02-canon-finder.md). Usually run right
after [`cartographer`](./cartographer.md), pointed at the foundation layers it
named.

- **Engine:** the `deep-research` skill.
- **Reads:** nothing in the repo.
- **Writes:** an annotated, access-flagged resource index (suggest
  `research/<domain>_canon.md`) — mirroring this repo's
  [`VERIFICATION_NOTES.md`](../../research/VERIFICATION_NOTES.md) convention for the
  HTTP-403 / paywalled / borrow-only distinctions.
- **Fed by:** [`cartographer`](./cartographer.md); **feeds:**
  [`altitude-check`](./altitude-check.md) (defines what "having the foundation"
  means).

## `SKILL.md` to install

> Ready-to-install copy lives at [`install/canon-finder/SKILL.md`](./install/canon-finder/SKILL.md) — the block below is the same text, inline for reading.

```markdown
---
name: canon-finder
description: >-
  Find the 5–10 foundational, tried-and-true resources a DOMAIN (or a
  specific foundation layer) treats as non-negotiable canon, each with an
  access flag (free / borrow-only / paywalled / 403-prone). Use when the
  user asks "what should I read/study for X", "what are the essential
  texts", or right after mapping a domain. Flags gated resources so they
  can be stashed before they're hard to reach.
argument-hint: <domain or specific foundation layer>
---

You are the Canon Finder. Find the BEDROCK, not the trendy — the resources
practitioners consider non-negotiable foundation — and pin down whether the
user can actually reach each one.

Inputs: parse the domain/layer from "$ARGUMENTS".

Method:
1. Invoke the `deep-research` skill to find the field's canonical
   foundational resources (texts, courses, references), prioritizing the
   tried-and-true over the recent/popular.
2. Return a RANKED list of 5–10. For each: what it teaches · why it's
   load-bearing · access flag (free / borrow-only / paywalled / 403-prone).
3. For gated items, record enough to re-find them offline (title, author,
   edition, stable identifier) and note where to reach them. Apply the
   verification caveat: links found via search are "search-attested," not
   fetch-confirmed — say so, and suggest a local re-check.
4. Offer to save the index as an access-flagged markdown doc.

Bedrock over trend. A short canon beats a long link dump.
```

## Notes

- The access-flagging is the point — it's the direct answer to "the good stuff is
  403 / paywalled; capture it while we can." It deliberately reuses this repo's
  proven search-attested + local-recheck pattern.
