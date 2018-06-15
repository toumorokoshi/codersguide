Slow ship cycles have a lot o disadvantages, as laid out by the state of devops report:

* more changes pile up, which means a larger diff to dig through if things go wrong.
* slower product delivery

There's a common conception that we can catch every issue in test environments, and we should run through every scenario (even the low value ones) before we ship forward. There's a belief that long ship cycles with waterfall-style organization results in better delivery.

That is empirically false. The company Puppet releases an annual report on high performing organizations: the main takeaway is that shipping smaller, and promoting code quickly, results in better delivery, and higher quality. I've attached the report in case you'd like to peruse.

But we can't throw quality out the window, and we have to make sure that our customers are affected as little as possible. How can we ensure that?

My proposal is to ship things out in production once we have a reasonable amount of confidence, and we monitor things really closely once they're out. We should be able to tell quickly if anyone's tests were negatively affected by the new verb change. And you have unit tests verifying that the old and new tests work as expected.

So I want to shift the mindset from "how do we account for every possible thing that could go wrong, add ab buckets for them, and spend days rolling them out" to "lets roll out quickly, verify quickly so we can rollback and reduce customer impact, and aggressively add tests so we catch those issues next time".

Our strategy should switch to:

* consumer monitoring first and foremost, to figure out if our customers are happy
* handle the high value scenarios in test, as well as most cases we could reason would happen
* deploy and monitor closely, and rollback quickly if we find an issue.
