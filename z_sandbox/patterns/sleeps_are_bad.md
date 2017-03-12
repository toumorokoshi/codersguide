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

Neither option sounds very attractive.

## An alternative: use a status call

The main issue arises from the indeterminate amount of time an
external resource takes to execute. In order for the test to act
appropriately, it needs to be able to accurately determine when
to continue.

To help the test, the SUT should provide some way to query the state
of a particular request. This will allow the test to determine the
status of an action, and wait until the result to verify is available.

For example, consider a service that reads entries from an incoming queue
and processes the output. One solution to testing this could be:

* add an entry to the queue
* sleep for X time
* validate the result

This could be converted to a more robust methodolgy:

* add an entry to the queue
* query the SUT for whether the entry is completed or not. block until
  validated.
* validate the result

## An Example

Let's say we have SUT that processes spreadsheets, and adds them into
a database. To interact with it, we have a webservice that provides:

* /process : an endpoint to POST a .csv file, which adds the file to the queue

To test that the process works as desired this would currently require
sleeps, because the
