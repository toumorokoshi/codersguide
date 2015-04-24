# Fullstack Testing

Some may wonder why UI testing a separate section from fullstack. Please refer to
the ui testing section to find out why.

Fullstack testing refers specifically to tests which test the full
infrastructure of a product. Examples include:

* a web service, including the UI, back-end server, and database
  interaction
* a desktop product, including the UI, any local filestorage
  interaction, and network interaction.

## Fullstack tests will not pass 100%

That's not necessarily true. But for a lot of products, it is. For a lot of fullstack tests,
100% success rates are not reasonable.

For example, let's consider a web-based product with three components:

* The front-end UI
* The back-end service
* The database

There's also other components in play that aren't directly related to
the product:

* network

Let's say that, individually, each component guarantees 99.9% success
rate when utilized. Now, when combined, the probability of a request
failing is 1 - the probability of all services succeeding:

    1 - 0.999^4 ~= 0.996

Given the current guarantees, a test against the product will fail 4 /
1000 times. If we start adding in other dependent components (an
analytics service, a third party service), the numbers become
worse. If we had 10 components at 99.9% success rate, we end up with:

    1 - 0.999^10 ~= 0.99

1 out of every 100 test executions will fail. And it will not indicate
a functional failure: each service is running within it's
specifications.

In addition, these test are often performed in test environments,
which often don't have nearly the same guarantees as a production environment.

Thus, it's reasonable to expect that these will fail, at least a small
percentage of the time. In situations like these, it's best to take a
running average and detect large fluctuations, rather than require a
100% pass rate. This is much easier to achieve on smaller tests such as
UI, integration, and unit tests.

## Fullstack tests are the least valuable test

In the section about cost, we talk about what increases and decreases
the value of tests. If you look at the value, fullstack tests are the
least valuable of all the tests.

Fullstack tests are slow, due to requiring setup and teardown of a
larger amount of state, and the number of steps required to fully perform
the test tend to be higher.

Fullstack tests are inconsistent, due to the number of components that
could be failing, multiplying the number of failures.

Fullstack tests are expensive to maintain, due to the constantly
changing component behaviour, and the upkeep of the components of the
product.

Fullstack tests require utilization of multiple resources, due to the way it must
propagate back and forth throughout the components.

It it is true that fullstack tests provide a lot of coverage. However,
when weighed against the increased expenses to execute and maintain
the test, investment in better testing of the isolated components is a
better use of people power.

## Fullstack tests are necessary

All of the above doesn't change the fact that fullstack tests do test
a vital part of the product that is not tested by the isolated
tests. Fullstack tests test the integration of all the components
together. Thus, choosing to omit fullstack tests entirely will lead
to a dangerous gap in coverage.

## But keep the count small

Ultimately, the actual area of coverage of a fullstack that could not
be potentially covered by a more isolated test is very small. As such,
it's best to keep the number of fullstack tests small.

These are expandend on in the 'patterns' part of the book, but some
good guidelines are:

* don't test variations in component behaviour in the fullstack tests
