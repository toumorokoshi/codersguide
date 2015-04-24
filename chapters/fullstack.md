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

## Fullstack tests are slow

In terms of time

## Fullstack tests are the least valuable test

In the section about cost, we talk about what increases and decreases the value of tests:

* the amount of functionality covered increases the value of a test, because
* the amount of maintenance required
* the amount
