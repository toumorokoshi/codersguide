# The Cost of Testing

## Why should we calculate the costs of tests?

Tests, like live software, have costs associated with them. These
costs are evident in a variety of factors:

* development time, to author the test
* development time, to maintain the test
* hardware, to run the test

For example, let's look a test that takes 10 minutes of dev time to
author, with an estimated 2 minutes / month to maintain, and requires
roughly 10 seconds of cpu time a month to execute after every build. This
would put a cost of:

* (10 / 60) * $50 = $8.33 initial
* (2 / 60) * $50 = $1.67 per month residual costs
