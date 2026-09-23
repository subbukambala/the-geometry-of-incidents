# Getting Started

Use this 30-minute exercise after the timeline and causal analysis are stable.
It adds an architecture-and-impact pass to the existing postmortem.

## Inputs

Bring:

- the incident timeline;
- user-impact or workload-impact metrics;
- a dependency or service diagram;
- mitigation and recovery milestones; and
- links to primary evidence.

Choose an incident the team already understands. Do not use the first session
to reopen a disputed causal investigation.

## Step 1: name one observable - 3 minutes

Write an explicit statement:

```text
Y-axis: failed checkout attempts
Population: all production checkout attempts
Aggregation: global, one-minute buckets
Time window: first failure through complete backlog clearance
```

If the data does not exist, record that limitation. Do not substitute a system
metric for user impact without labeling the change in perspective.

## Step 2: mark impact milestones - 5 minutes

Record:

- first known disturbance;
- first user impact;
- peak breadth and depth;
- containment;
- primary service restoration;
- residual work or state clearance; and
- full confidence or incident closure.

In many incidents, "mitigated" and "recovered" are different timestamps.

## Step 3: walk through TRACER - 10 minutes

Use [`templates/tracer-review-template.md`](../templates/tracer-review-template.md).
For each stage, distinguish direct evidence, inference, and unknowns.

Ask:

1. **Trigger:** Where did the initial instability begin?
2. **Route:** Which architectural paths carried it?
3. **Amplification:** What increased scale, speed, depth, or persistence?
4. **Consequence:** Which users, operations, and regions were affected?
5. **Extent:** What limited the incident's extent, and which boundary failed?
6. **Recovery:** How did service, correctness, and accumulated work return?

## Step 4: classify three layers - 5 minutes

Record separately:

- the observable's curve;
- the supported causal geometry or geometries; and
- supporting architectural properties.

Do not assign one permanent shape to the whole incident. A cliff in user errors
can coexist with a retry feedback loop and a long recovery tail.

## Step 5: convert findings into tests - 7 minutes

For each important observation, complete this chain:

```text
Observed evidence
-> architectural hypothesis
-> protection needed
-> proposed control
-> verification test
```

Example:

| Evidence | Hypothesis | Control | Verification |
| --- | --- | --- | --- |
| Bad content reached most eligible hosts before responders could act | Propagation outran human response | Staged deployment with automatic safety gates | Inject an invalid canary update and verify promotion stops before the next ring |

## Definition of done

The review is useful when another engineer can:

- identify the observable and evidence;
- distinguish curve from mechanism;
- challenge the classification;
- see which boundary is implicated; and
- execute or evaluate the proposed verification test.

## Next step

Compare the completed review with
[`case-studies/crowdstrike-2024.md`](../case-studies/crowdstrike-2024.md),
then add a row to the
[`incident-coding-template.csv`](../templates/incident-coding-template.csv).
