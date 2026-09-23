# Limitations

Version 0.1.0 is an operational review framework. It is neither a complete
taxonomy nor a predictive model.

## A curve does not prove a cause

Different architectures and mechanisms can produce similar time-series curves.
A sawtooth may result from unstable failover, repeated rollback, capacity
cycling, or several other mechanisms. Geometry should generate and organize
hypotheses; causal claims require architectural and timeline evidence.

## Classification depends on the observable

The same incident can be a slow burn in resource margin, a cliff in failed
requests, and a long tail in affected tenants. Every classification therefore
depends on the named y-axis, population, aggregation, and time window.

## Public reports are incomplete evidence

Operator reports are written for different audiences and disclose different
levels of architecture, timing, and customer impact. Missing evidence cannot be
treated as evidence that a mechanism or boundary was absent.

## The starter corpus is selected, not representative

The initial cases are information-rich, public, large-scale incidents chosen to
illustrate the framework. They do not establish prevalence across all incident
types, organizations, or system scales.

## Retrospective analysis has hindsight bias

Post-incident explanations can make propagation paths appear more obvious than
they were during response. Reviews should record what responders knew at each
stage and avoid converting later knowledge into claims about real-time
diagnosability.

## Terms may overlap at stage boundaries

Fan-out can lead to a cascade; synchronization can close into a feedback loop;
recovery can become a new trigger. The vocabulary is intended to preserve these
transitions rather than force one mutually exclusive label.

## Measurement may hide segmentation

Global averages can conceal complete failure for a small population. Report
relevant tenants, regions, workflows, platforms, cohorts, and percentiles when
the evidence permits.

## No demonstrated prevention effect yet

There is no controlled or longitudinal evidence that using this framework
reduces incident frequency, severity, or recovery time. Until that evidence
exists, evaluate it on narrower outcomes: whether reviews define impact more
precisely, expose a missed containment assumption, or produce a testable design
change.

## Security, integrity, and safety incidents need extensions

The six-stage flow can be applied beyond availability, but confidentiality,
integrity, adversarial adaptation, and physical safety may require observables
and causal concepts not represented in this initial vocabulary.

## Planned validation

Validation requires the following work:

1. publish explicit coding rules and inclusion criteria;
2. expand the incident corpus;
3. have independent reviewers classify a representative sample;
4. measure and report agreement and disputes;
5. revise definitions using counterexamples; and
6. study whether resulting actions differ from conventional reviews.
