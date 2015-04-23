# UI Testing

For most products, you will have a portion of it that is exposed to
and end user. Someone who will have no understanding of how your
product works, and only interacts with it via regulated experiences
that you dictate.

To ensure shipping a quality product, it's important to test this area
as well. However, UI testing can be more complex than testing code
directly: you must have some mechanism by which to automate user
interaction.

## UI Tests are not Full Stack Tests

A common misconception surrounding UI tests is that they need to
interact with the full stack. Although it is possible to test the full
stack while testing UI, this is not necessary, and can ofter lead to
inconsistent results on what should be very consistent,
straightforward tests.

## Why UI Tests are 'Flakey'

Inconsistency (commonly refered to as flakey) is a term that is
associated with UI tests often. Inconsistency can be avoided by
following the same basic tenants that one would with unit testing:

* stubbing dependencies that can have inconsistent results
    * web services
    * databases
* keeping the validation small
    * don't test multi-step workflows in one test

Inconsistent UI tests tend to have the same symptoms as bad unit tests:
making multiple assumptions on the existing state, and following complex workflows
that require multiple steps.

There are strong corollaries between UI tests and unit tests for a reason: because UI tests are another
form of unit testing.
