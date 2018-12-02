# Measures for IT Efficiency

https://www.youtube.com/watch?v=EmDtmYwDs50&t=404s

## Throughput

* lead time for changes
* release frequency

## Stability

* time to restore service (MTTR)
* change fail rate (MTBF)


# Targets

* Deploy Frequency: on demand
* commit to production: less than one hour
* MTTR: less than one hour
* change failure rate: 0-15%

# Effective Test Practices

- Developers primarily create + maintain acceptance tests
- When automated tests pass, confident that software is releasable
- Test failures likely indicate a realy defect
- Easy for developers to fix acceptance tests
- Developers share a common pool of test servers to reproduce failures
- Developer use their own dev environment to repro failures

## These don't cause statistically significant improvements:

- QA primarily create & maintain acceptance tests
- Primary created and maintained by outsourced party
- Developers create on demand test environments

# Other Conclusions

* managing WIP is negligable (by itself)
  - works w / visual displays
