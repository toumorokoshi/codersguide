# Don't mind this section...

Design should be building the technical primitives, then building the right contextual abstractions.

Design harmony is when the two match.

Symptom vs cause

# Useful Alerts

Components:

* generating strong signal
* identifying severity of signal

# Paging

Pages should occur out of impact to the user.

## Paging should be based on the severity of the impact to the user.

* impact to the user needs to be consistent (e.g. continuous flow of 500s vs a dripping faucet of 500s).
  * continuous flow may need action today
  * a dripping faucet can probably wait until the next business day.

## Eliminate Redundant Alerts

# Types of Alerts

* Shit is failing now: significantly degraded user action
* Papercuts: not an indicator of hugely degraded user action, but bad
* About to fall off a cliff: an alert is closing in on a threshold that needs action

## Actions

### About to fall off a cliff

React before the cliff falloff happens

### Papercuts

React when reasonable

### Shit is failing

React now



# Argos

Uber Argos (optimizing for reaching significance with alerting)

* automated anomaly detection calculation
* outliers feed into algorithm which considers:
  * similar trendlines and if they are outliers as well
  * count


## Distinguish Between Positive and Negative Outliers?

## Outlier Categorizations

### Additive Outliers

Bumps in traffic, unexpected growth

### Temporal Changes

A low or zero metric input for  short period of time

## STL Decomposition

STL decomposition splits a metric into three separate graphs

* seasonal: periodic, non-changing
* trend: a larger overall trend of the meric itself
* residue: the leftovers


## Random

Produce a system that analyzes the metric after an initial influx of data (10 days?) and then uses that to make an educates guess regarding anomalies.

The user selectst the anomalies, and the best algorithm choice that captures that anomaly is selected?
