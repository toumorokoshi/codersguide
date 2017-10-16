# Use histograms, not p99.

## What is pXX?

pXX (e.g. p50, p95, p99) is a measurement system that defines the boundary at which that a particular percentage of data points fit within that threshold.

For example, p95 for max latency represents the latency at which 95% of traffic is below.

## What is a histogram?

A histogram is a concept in monitoring that buckets a data point into a predefined set of buckets. For example, all latency requests could be categorized in a buckets of:

* < 100ms
* 100 < 300ms
* 300 < 1s
* 1s < 10s
* 10s <

## Why are histograms better than pXX?

### Histograms can be aggregated

pXX metrics are percentiles, which mean that there's no reasonable way to aggregate those data points. The strategies available to you are inaccurate, in one way or the other.

* weighted average: weighted average does not handle anomalies properly

Histograms can be aggregated across multiple data sources easily: just sum!

This property alone makes pXX a bad choice for monitoring systems. There is no way to subdivide your monitoring and aggregate: getting an accurate p99 means creating a system than ingests EVERY SINGLE data point at a single source.

### Histograms give better context to the "shape" of traffic.

Any percentile loses granularity into the actual behavior of the users. The following situations result in equivalent p99:

* 98 1ms, 1 1s, 1 10s
* 98 900ms, 1 1s, 1 10s

### Storing histograms in memory is cheap

Histograms are simply points aggregated into buckets: it can be representing with a single hashmap of <string, int> pairs. The calculation to add a metric is also just incrementing a value in a hashmap. If you wanted to optimize even more, you could store it as an array and reduce operations on the cpu.

Any programming language can implement this quickly. p9x requires storing all data points, or using an algorithm to effectively guess at the accurate value.

## How to build good histograms

Histograms require something pXX doesn't: choosing good boundaries beforehand, and also number of boundaries. Let's talk about these issues separately.

### Choosing Good Boundaries

Boundaries are best when they are meaningful: there is a real impact on an aspect of your service that you care about. For example, let's look at latency as an example. Latency has a few core points:

- < 300ms: page loads are impercievable to a common user

https://www.forbes.com/sites/jiawertz/2017/03/17/how-to-compete-for-consumers-online-while-attention-spans-diminish/#599dc1146667

### How many Boundaries

This question is less important. Most metrics storage systems worth their salt can store millions of metrics, so the number is really a matter of what makes sense from a business perspective.


## More Reading

* https://www.wavefront.com/why-histograms-critical-for-reporting-hi-velocity-metrics/
