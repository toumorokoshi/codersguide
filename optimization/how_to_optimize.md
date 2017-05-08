# How To Optimize

## Short and Sweet

1. figure out the most expensive part of your system
2. figure out how to make it more efficient

## In Detail

### 1. figuring out the most expensive part

Optimization has one goal: making a process more efficient. The KPI
is how efficient your process is:

* how fast it takes to execute a task
* how many tasks can be executed concurrently

With that KPI in mind, the must successful optimization is the one
that increases efficiency the most.

<!-- TODO: site -->

The Pareto Principle shows that 80% of the work is typically done by
20% of the process. Thus, it's just as important to figure out where
an optimization needs to happen, as the optmization itself.

In software, profilers (Python: cProfile) can be used to benchmark
code and see where the cost is.
