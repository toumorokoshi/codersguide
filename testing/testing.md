# Testing

- instability estimate of full-stack tests.
- testing pyramid
  - cost of a test
- testing feedback loop

## TLDR

- as many unit tests as possible
- as few integration tests and full-stack tests as possible
- code coverage isn't a perfect metric of defect detection. Test count is better.

## The Details

### What do we want from tests?

The most valuable tests provide the most coverage
for the smallest developer cost.

as of 2016, hardware is relatively cheap (ELABORATE)

#### Fast Feedback
#### Stability


# Working Backwards (MTTR, MTBF, MTTD)

It's often the case to examine testing as a problem in isolation, but
starting with the goal, as with product design, helps testing as well.

A  successful testing  process is  one that  helps reliability  of the
product(s)  provided by  your team.  Using the  common KPIs  for SRE's
works great as KPIs here:

* MTBF (Mean Time Between Failure): mean time between issues in production
* MTTR (Mean Time To Recovery): time to recover from an issue, once discovered
* MTTD (Mean Time To Detection): time to find that an issue exists

How does testing affect these KPIS?

## MTBF

If bugs are caught before they are shipped, then that is a failure
that does not ship to production. Assume that all regressions come
in at some frequency N. If we increase the likelyhood of finding bugs in test
by 10%, then or frequency reduces to 0.9N.

MTBF = 1 / N. So assuming that N = 10 regressions / 30 days, decreasing that to 9 results in:

    MTBF_OLD = 1 / (30 days / 10 regressions) = 3 days
    MTBF_NEW = 1 / (30 days / 9 regressions) = 3.3 days

## MTTR

Mean time to recovery is helped with more granular monitors, as the
root cause becomes quicker to detect.

## MTTD

Mean time to detect is helped with more monitoring, as the root cause
is discovered quickly.
