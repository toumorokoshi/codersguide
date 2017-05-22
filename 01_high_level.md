# High Level: The 1000 foot view on software engineering

<!-- TODO: link -->

# The ultimate goal of software is to provide value

The most efficient software teams are those that provide the most
value to the customer. There are three core KPIs for providing user
value:

## Choosing the right projects

1/3rd of projects measured against a KPI actually improved the KPI
when release. Based on that study, 2/3rds of projects executed do not
have the desired effect, and may not have any effect. Thus, choosing the
right project to deliver is important.

## Mean Time To Delivery of Functionality

Mean time to delivery is the amoutn of time it takes to deliver
functionality. It would be best to measure it as the amount of time
from when work is started on the task, to when it is delivered.

Measuring from time when it is requested is a fallacy, as the amount
of work your team has in the queue can impact this. Time in queue (and
value of projects in queue) is a better KPI for whether more resources
should be allocated to the team.

## Mean Availability

In this case, availability is defined as the total amount of time your
software is providing value to your users, vs the total amount of time
that value is desired. If there is a point in time where a user wants
to extract value (e.g. use your application), and your software is
unavailable or unable to provide that value, that negatively impacts
this KPI.

# Improving Project Choice

See the Lean Startup.

# Improving the Pipeline, and ensure high mean availability

Assuming optimal project choice, the next item to optimize is the
delivery of software.

* Project Begins
* Write Code
* ?
* Project Delivered

In order to measure if the project delivery was
successful, it's important to define the project to a point that
acceptance criteria can be outlined about the functonality and
availability of the project.

We'll define a project as delivered when:

* all acceptance criteria has been met
* the project is available to all desired customers

The delivery of code to customers is typically called deploy:

* Project Begins
* Write Code
* ?
* Project Satisfies Acceptance Criteria
* Deploy
* Project Delivered

To ensure that mean availability remains high, the acceptance criteria
must be validated BEFORE the deploy. To ensure this, there must be a
comprehensive execution of acceptance tests performed:

* Project Begins
* Write Code
* ?
* Run Acceptance Tests
* Deploy
* Projects Delivered

At this point, the pipeline could be considered
complete. Unfortunately, it is often the case that code does not pass
all acceptance criteria upon Write. Thus, the cycle looks something like:

1. Write Code
2. Run Acceptance Tests
3. Failed, Write Code
4. Run Acceptance Tests
5. Failed, Write Code
6. Run Acceptance Tests
7. Deploy

Thus, the speed of the pre-deploy cycle is significantly more
important than the speed of the deploy itself. Acceptance criteria
tends to require full test environments or more test fixtures, and
there are much cheaper alternatives, like unit testing. Thus, it makes
sense to introduce unit testing as a much cheaper way of providing
feedback:

1. Write Code
2. Run Unit Tests
3. Failed, Write Code
4. Run Unit Tests
5. Run Acceptance Tests
6. Failed, Write Code
7. Run Unit Tests
8. Run Acceptance Tests
9. Deploy

If we assume that we saved even a single acceptance test run by a unit test, then you break even when:

    acceptance_time * num_times > acceptance_time * (num_times - 1) + unit_time * num_times
    acceptance_time > unit_time * num_times
    acceptance_time / num_times > unit_time

So, if your average pass includes running 5 acceptance passes, then
you will save time if your unit tests take 1 / 5th of acceptance time.

In practice, you save many times that amount, as one iterates rapidly
on unit tests, and ends with a single execution or two of acceptance
tests. If we assume:

* acceptance_time = 10 (min)
* unit_time = 1 (min)
* num_times = 5

Then the time savings is:

    with only acceptance: 5 * 10 = 50 minutes
    with unit tests, 1 failed acceptance run: 2 * 10 + 5 * 1 = 25 minutes
    with unit tests, 0 failed acceptance run: 2 * 10 + 5 * 1 = 15 minutes

The savings on the pipeline is over 50 percent! In practice, unit
tests are much, much faster than acceptance tests, and the iteration
cycle can be far more than 5 times, so higher yields are not unusual.

Thus, a bare-minimum software delivery pipeline looks like:

1. Write Code
2. Run Unit Tests
3. Run Acceptance Tests
4. Deploy

Making this loop more efficient is a matter of seeing where tooling or
practices can be applied to provide an objective improvement. This is
a kind of product design of it's own, and could benefit from the lean
startup assumption validation framework.

A common pattern comes in automation: a majority of this pipeline can
be automated:

1. Write Code
2. (Automated) Run Unit Tests
3. (Automated) Run Acceptance Test
4. (Automated) Deploy

The goal is to ensure that developers are dedicating as much time as
possible to creating value. This is done by meticulously identifying
automatable tasks, and automating them.

This basically amounts to the philosophies of continous delivery.
