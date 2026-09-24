# Try Incident Geometry in 5 Minutes

This exercise is a fast test of the method, not a substitute for a full
incident review. You need only a familiar incident and five minutes.

## First, see the result - 1 minute

The 2024 CrowdStrike Falcon incident can be summarized as:

```text
Observable: Windows hosts unable to operate normally
Origin: A problematic content update exercised a latent sensor defect
Propagation: Central content distribution reached eligible Windows hosts
Amplification: Broad automatic distribution and privileged execution
Impact: Affected hosts crashed; platform and exposure timing limited the scope
Recovery: Withdrawal stopped new exposure, but affected hosts needed separate repair
Test: Inject an invalid canary update and verify promotion stops before the next ring
```

The defect explains why one host crashed. The distribution and recovery paths
explain why impact spread quickly and repair took much longer.

Read the [complete case study](../case-studies/crowdstrike-2024.md) when you want
the evidence, confidence, and competing-interpretation detail.

## Now trace one of your incidents - 3 minutes

Use one sentence for each prompt. Record `unknown` instead of filling an
evidence gap with an assumption.

1. **Observable:** What user- or workload-visible quantity changed?
2. **Origin:** Where did the initial disturbance begin?
3. **Propagation:** Which dependency, rollout, queue, routing, or automation
   path carried it?
4. **Amplification:** What made the impact larger, faster, deeper, or more
   persistent?
5. **Impact and containment:** Who experienced it? Which boundary held, failed,
   or was missing?
6. **Recovery:** What restored service, correctness, and accumulated work?

## Turn one finding into a test - 1 minute

Complete this chain for the most consequential observation:

```text
Observed evidence
-> architectural hypothesis
-> protection needed
-> proposed control
-> verification test
```

If you can name a test that could disprove the protection, the exercise has
produced something actionable. If the six prompts expose disagreement or
missing evidence, that is also a useful result.

## Continue

- Run the [30-minute review](getting-started.md).
- Copy the [full review template](../templates/tracer-review-template.md).
- Compare your result with the
  [CrowdStrike case study](../case-studies/crowdstrike-2024.md).
