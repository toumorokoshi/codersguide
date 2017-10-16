# A top-down philosophy on alerting

## What is an alert, and what is it good for?

Alerts are a way to be notified automatically of a situation that requires human action. Alerts are composed of:

* a monitor: a way to observe data that could signify the need for human intervention
* a criteria: a way to analyst the data to determine if human intervention is needed


# When is human judgement necessary?

## When there's a massive change in service behavior?

A change in service behavior could signify either a system behaving incorrectly,
or a system that is now experiencing an abnormal situation.

Abnormal situations could become the new normal with little fanfare. But,
abnormal situations might require human intervention to handle as well (e.g.
  someone increases load 10x)

If a system is architected in such a way that it can scale with load, then
it just becomes a matter of scaling relative to the demands of the service.
scaling hardware becomes a matter of cost. The ultimate decision maker should
be the person responsible for deciding if the budget of the system is reasonable or not.

200 counts are only a problem if the usage is "too high." What is too high?

* the system becomes close to approaching a cliff (eventual resolution)
* the system is too costly (eventual resolution)
* the system is falling off a cliff (immediate resolution)

## Alert Priorities

There are three major priorities to alerts:

* alerts that must be investigated now
* alerts that must be investigated soon
* alerts that must be investigated eventually

In either situation, they must be investigated. The alerts
that need to be investigated in the future could be batched and investigated separately.

### Alerts that need to be investigated now

AKA: Excuse me from the dinner table

Notification Strategy: Page

* user impact below SLA

Examples:

* system unavailable

### Alerts that must be investigated soon

AKA: I'll look after dinner

Notification Strategy:

*  Page during business hours
*  Page lower priority off-hours (with specification that this is a "soon")

* likely user impact impending

Examples:

* host down?

#### Why should we differentiate between this and "now"?

Because soon and now are a huge quality of life difference. This is a human comfort threshold more than it is a threshold about system operations.


### Alerts that must be investigated eventually

AKA: I'll look at it on Monday

Notification Strategy: E-mail, or no notification. Separate dashboard

Could be batches together for a single investigation with others, saving time from context switching.

* no likely user impact, or minimal user impact

Examples:

* single 500s error
* high 200s

## Who should investigate these alerts?

Each of these categories require investigation. The question is who.

For Now + Soon, we need fast responses. Fast responses can cause significant fatigue,
 so it's important to share the burden on these. So, on-call rotation

For eventually, we're talking about someone looks at the situation periodically,
and makes judgements based off of that. We could assign it to a single person responsible for quality, or share that burden as well.

## Alert Types

### Business SLA

A business SLA reflects a critical business metric. A degradation before

## Achieving Strong Alert Signal

## Questions

### Should alerting be the same alert on a continuum, or multiple static alerts?

An monitor could emit one of the three severities (now, soon, eventually)

now: 10+ 500s
soon: 3+ 500s
eventually: 1+ 500s
never: pass or green?

An alert could implement only one of the three.

### How to visualize the different alert categories?

### Should alerts be in code? Should they follow the service?

Alerts following the service has been really valuable, because the service changes. The alerts following the service that changes makes a lot of sense.

But there are also alerts that have to do with the environment the service is a part of:

* traffic
* total cpu
* total memory

These alerts should be quickly tunable, or live with a separate system that determines the user traffic.

^ Dynamic loading from config-values for faster action?
^ temporary override?

### It's lame that we have to ship a service to make a monitor change.

Monitors should live with the service, but we shouldn't have to ship the whole thing to make a change.

We should probably allow temporary changes

### Validation for promotion and alerting in production are fundamentally different?

validation for promotion: everything is working.
alerting in production: response is variable depending on severity.

## Links

https://www.datadoghq.com/blog/monitoring-101-alerting/
