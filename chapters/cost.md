# A shorter test is more valuable

At it's core, a test exists to verify functionality. When working in
an environment that emphasizes rapid development, it's important to
get feedback as soon as possible. Shorter tests provide feedback more
quickly than slower tests. The slower a test is, the more likely it is
to run in a process that is farther removed from a developer's
standard development process.

One can also execute shorter tests far more rapidly that larger tests. For example, let's say that, on average:

* a unit test takes 1ms
* an integration test takes 100ms
* a full-stack tests

# What costs are associated with a test?

* maintenance cost
* time to execute
* resources consumed during execution
