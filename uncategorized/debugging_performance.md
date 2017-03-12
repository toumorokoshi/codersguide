# Debugging Performance

This chapter is good for:

Debugging performance comes down to:

1. identify the bottleneck
2. alleviate the bottleneck

Here's some areas to check:

## CPU

You can look at `top` and see if your CPUs are running at 100%. If so,
your CPU is a bottleneck.

### Can your process take advantage of multiple CPUs?

Some applications cannot take advantage of multiple CPUs, mainly as a
byproduct of it's implementation. Many scripting languages do not support multiple CPUs:

* CPython (kind of: Python bytecode can only execute one thread at a time per process)
* NodeJS
* Ruby

In this situation, a single CPU running at 100% could be an indicator
of a bottleneck.

## Memory

## IO
