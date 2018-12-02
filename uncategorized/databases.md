# Databases, Fast and Slow.

When working with databases, here's a few core principles to help you
ensure performance.

## Index Queries are Fast

Any database query that utilize an index will be orders of magnitude
faster than a scanning query.

For a single document, finding it using and index is
O(Log(collection\_size)), and without an index is O(collection_size).

## All-data-in-index Queries are even faster

There's also a significant improvement in a query retrieving all
desired data completely satisfied by the index. Due to only having to
access and build records from one position in memory (vs a second
lookup, once for the index, and once for the data itself), you save a
lot of lookup cost.

## Scanning Queries are slow

Queries that require scanning documents for data is very slow. Only
reserve this for really slow queries.
