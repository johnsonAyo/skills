---
name: replace-dont-layer
description: Change code at the existing behavior owner instead of accumulating parallel implementations, overrides, compatibility branches, or duplicate tests. Use for implementation, bug fixes, refactors, styling changes, reviews, and multi-agent coding whenever code already influences the requested behavior.
---

# Replace, Don't Layer

Produce one coherent implementation of each behavior. Treat the codebase after the change—not the size of the patch—as the unit of quality.

## 1. Find the behavior owner

Read available `CONTEXT.md`, architecture notes, and ADRs for orientation. Then search the code itself; documentation is not an inventory.

Trace the requested behavior through its routes, callers, interfaces, configuration, styles, tests, and active changes. Search by user-facing text, domain terms, symbols, paths, selectors, and related test descriptions. When multiple agents are active, inspect their work and establish which implementation owns the seam.

Complete this step only when every discovered implementation of the same capability is accounted for and you can name the current behavior owner.

## 2. Choose the smallest coherent change

Prefer, in order:

1. Modify the behavior owner.
2. Deepen or generalize it so existing callers share the change.
3. Consolidate competing implementations.
4. Replace the owner and remove the superseded path.
5. Add a new path only for a genuinely new capability or seam; state why the existing owner cannot contain it.

Inspect the full causal slice, but edit only the smallest coherent slice that owns the behavior. Record unrelated problems separately.

Preserve compatibility only for an evidenced consumer, stored-data contract, or staged migration. Give retained compatibility an owner and a removal condition.

## 3. Change production code and tests together

Treat tests as part of the implementation history. Before adding a test, find tests at the same behavioral seam. Update, merge, replace, or delete overlapping tests; keep separate cases only for distinct contracts.

Implement until the behavior has one authoritative path and the tests describe the current contract rather than the sequence of past implementations.

## 4. Verify and remove residue

Run the narrowest relevant checks while working, then the appropriate full verification.

Audit the diff and search for residue from the superseded behavior: old branches, duplicate pages or services, selectors, tokens, flags, adapters, configuration, comments, fixtures, compatibility mappings, and tests. Remove each obsolete item or document why it remains and its removal condition.

Completion requires both correct behavior and an account of every superseded path. Passing tests alone is insufficient.

## Handoff

Report concisely:

- The existing behavior owner.
- What was modified, consolidated, replaced, or removed.
- Any genuinely new code and why it was necessary.
- Tests updated, merged, or deleted.
- Compatibility intentionally retained and its removal condition.
