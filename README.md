# FEP-c195: JSONPath Filtering for ActivityPub Collection Retrieval

**Status:** DRAFT · **Type:** implementation · **Author:** Steve Bate

## Overview

This FEP defines a `filter` query parameter for retrieving ActivityPub collections. The
parameter takes a [JSONPath (RFC 9535)](https://www.rfc-editor.org/rfc/rfc9535) expression
that is applied to a collection's item array (`orderedItems` for ordered collections,
otherwise `items`) or to the items of a shared-inbox pseudo-collection.

A server following the proposal:

1. Selects the items the authenticated actor may view (public, addressed to the actor, or
   attributed to the actor).
2. Applies the JSONPath expression to those items.
3. Returns the matches as an ActivityPub collection, optionally paged and under a result URI
   unique to the filtering operation.

A filter without a leading `[` is treated as an item-level predicate and wrapped in
`[?…]`; one beginning with `[` is used as-is, allowing projections and other features.
Implementations must support at least root and child selectors, wildcards, filter selectors,
comparisons, and boolean operators, and must reject invalid filters with a client error.

## Files

- [`fep-c195.md`](fep-c195.md) — the proposal

## The FEP

- Document: <https://github.com/steve-bate/fep-c195-jsonpath-filtering/blob/main/fep-c195.md>
- Repository: <https://github.com/steve-bate/fep-c195-jsonpath-filtering>
- Discussion: <https://github.com/steve-bate/fep-c195-jsonpath-filtering/issues>

## License

This work is released under [CC0 1.0 Universal](LICENSE.md) (public domain dedication).
See [LICENSE.md](LICENSE.md).
