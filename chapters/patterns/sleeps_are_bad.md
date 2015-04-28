# Pattern: Eliminating Sleeps

Sleeps are any phase in a test in which a test is paused for a
pre-designated period of time.

## When to use the pattern

When there are sleeps in your test

## Why are sleeps bad?

Sleeps come from a need to wait until a certain condition is satisfied:

* an action perfomed on a web page that needs to wait for that action to take effect
* an action against a service requires those changes to propagate through a queue service

In a majority of cases, the amount of time it takes for these effects
to occur are variable: the actual time taken could vary based on the
load against the product, or the network connectivity, or some other
factor involved the proper function of the product.

This leads to a choice made about the wait:

* to lengthen the amount of time to wait until the absolutely acceptable maximum, which
  increases test execution time.
* to choose a more reasonable amount of time, and accept that the test
  will be inconsistent.

Neither option sound very attractive.

## An alternative: use a status call or callback

The main issue arises from the indeterminate amount of time an
external resource takes to execute. In order for the test to act
appropriately, it needs to be able to accurately determine when
to continue.
