# The Geometry of Incidents Framework

## Definition

The geometry of incidents traces a failure through a distributed system: where
it started, how it propagated, what amplified it, where users felt it, what
contained it, and how the system recovered.

The method connects two views:

- **Impact dynamics:** what a named user-impact observable does over time.
- **Architectural causality:** how system structure transforms an initiating
  disturbance into that pattern of impact and recovery.

The working proposition is:

> The shape of an incident is produced by the architecture.

An impact curve is evidence, not a diagnosis. The architecture and timeline
must support any causal claim.

## Six stages

Analyze each incident in this order:

```text
Origin -> Propagation -> Amplification -> Impact -> Containment -> Recovery
```

### 1. Origin

Where did the initial disturbance begin? The origin can be a process, host,
dependency, deployment, region, tenant, configuration, or control-plane action.
It is not necessarily the component users observe as broken.

### 2. Propagation

How did the disturbance travel from the origin to user-visible impact? Relevant
paths include dependency calls, configuration distribution, queues, routing,
shared databases, service discovery, automation, and client reconnection.

### 3. Amplification

What made the disturbance larger, faster, deeper, or more persistent? Common
amplifiers include retries, synchronized work, feedback loops, accumulated
backlogs, health automation, resource contention, and failover concentration.

### 4. Impact

Who or what experienced the failure? Describe exact users, tenants, workflows,
operations, regions, traffic classes, or resources. Name the denominator rather
than reporting an isolated percentage.

### 5. Containment

Which boundary stopped the failure, failed to stop it, or was missing?
Boundaries include cells, regions, tenant quotas, deployment rings, priority
classes, independent control planes, circuit breakers, and degraded modes.

### 6. Recovery

How did the system return to health? Record restoration order, throughput,
backlog, reconciliation, recurrence, manual work, and any difference between
time to containment and time to complete recovery.

## TRACER mnemonic

TRACER is a mnemonic for the formal stages, not a second taxonomy.

| TRACER | Canonical stage | Prompt |
| --- | --- | --- |
| Trigger | Origin | Where did instability begin? |
| Route | Propagation | Which paths carried it? |
| Amplification | Amplification | What increased its scale or persistence? |
| Consequence | Impact | What did users or workloads experience? |
| Extent | Containment | What limited its extent, and which isolation boundary failed? |
| Recovery | Recovery | How did service and correctness return? |

## Five impact dimensions

Measure observable impact with five questions:

| Dimension | Question | Example measure |
| --- | --- | --- |
| Breadth | How wide? | Percent of active tenants affected |
| Depth | How bad? | Failed operations or blocked workflow |
| Duration | How long? | Time to contain and time to full recovery |
| Speed | How fast? | Time from origin to peak breadth |
| Recovery | How back? | Time to 90%, 99%, and complete restoration |

Breadth, depth, and duration describe the size of impact. Speed and recovery
describe how the system entered and left that state. Record values over time
where the evidence allows it. Peak breadth multiplied by total duration often
overstates cumulative impact.

## Three-layer classification

Do not combine these three layers:

1. **User-impact curve:** cliff, slow burn, wave, plateau, sawtooth, or
   long-tail recovery.
2. **Causal geometry:** fan-out, cascade, feedback loop, or synchronization.
3. **Supporting properties:** boundary crossing, containment breach,
   control-plane/data-plane coupling, shared-resource spillover, asymmetric
   impact, or propagation front.

Every curve must name its observable. A queue-depth slow burn can coexist with
a cliff in failed user requests; these are different measurements, not a
classification conflict.

## Minimum Geometry of Incidents statement

A review should be concise enough to summarize like this:

```text
Observable: Windows hosts unable to operate normally
User-impact curve: Cliff followed by long-tail recovery
Causal geometry: Centralized fan-out
Amplification: Privileged execution and broad automatic distribution
Containment: Platform and connectivity boundaries held; deployment rings did not
Recovery: Withdrawal stopped new failures; affected hosts required separate repair
Confidence: High for mechanism, medium for population over time
```

## Relationship to existing analysis

Use the Geometry of Incidents alongside:

- **Timelines**, which establish sequence.
- **Root-cause analysis**, which explains initiating conditions.
- **Fault trees and FMEA**, which reason about failure combinations and modes.
- **Blast-radius analysis**, which measures affected scope.
- **SRE and resilience reviews**, which establish operational and design action.

The added output is a traceable connection between the impact curve, the causal
paths, the boundaries observed under stress, and the recovery path.

## Related terminology

The phrase *incident geometry* is also used by Willie Wheeler for a
[graph-spectral approach to incident propagation](https://williewheeler.com/posts/why-service-topology-constrains-failure-states/).
That work represents service signals in topology-derived propagation modes.
The Geometry of Incidents is a qualitative review method that connects a named
impact curve to propagation, amplification, containment, and recovery. The two
approaches share an interest in topology-constrained failure behavior, but they
answer different operational questions.

## Review output

A completed review should produce:

- one clearly defined observable;
- a sourced fact record;
- six stage findings;
- a curve classification and one or more causal geometries;
- working and failed containment boundaries;
- competing interpretations and confidence;
- engineering controls tied to specific findings; and
- a test that could falsify the team's assumptions.
