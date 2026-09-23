# Vocabulary

Incident reviews often use one label for a curve, a mechanism, and an
architectural property. Keep those claims separate.

## User-impact curves

These terms describe what a named observable does over time. They do not, by
themselves, identify a cause.

| Curve | Required observation | Does not imply |
| --- | --- | --- |
| **Cliff** | The observable moves abruptly from healthy to severe impact. | A global outage or any particular deployment mechanism |
| **Slow burn** | The observable deteriorates gradually over a meaningful interval. | Resource exhaustion as the only cause |
| **Wave** | Impact or activity forms a concentrated or rolling peak. | Synchronization unless evidence shows aligned actors |
| **Plateau** | Impact remains at a broadly stable elevated level. | Stable internal system state |
| **Sawtooth** | Impact repeatedly improves and worsens. | A control-loop defect without corroborating evidence |
| **Long-tail recovery** | Most impact contracts, but a residual population persists substantially longer. | Any single repair bottleneck |

### Recovery language

- **Sharp recovery:** an abrupt improvement after containment.
- **Progressive recovery:** impact declines gradually by capacity or cohort.
- **Recovery wave:** recovery work forms a concentrated peak.
- **Sawtooth recovery:** mitigation and relapse alternate.
- **Long-tail recovery:** residual users, objects, or work recover slowly.

These are stage-qualified readings of the same curves, not a second taxonomy.

## Causal geometries

These terms describe how failure spreads or reinforces itself.

### Fan-out

One source or shared dependency directly affects multiple otherwise partly
independent consumers.

```text
Shared source -> Consumer A
              -> Consumer B
              -> Consumer C
```

Evidence includes converging dependency paths, correlated onset, or several
consumers recovering when one shared dependency is restored.

### Cascade

Failure moves sequentially through dependent stages, and changed state in one
stage materially changes conditions for the next.

```text
A -> B -> C -> D
```

Temporal succession alone is insufficient; the causal dependency must be
supported.

### Feedback loop

The system's response reinforces the failure. For example, latency causes
timeouts, timeouts cause retries, and retries create more latency.

```text
Latency -> Timeout -> Retry load
   ^                     |
   +---------------------+
```

### Synchronization

A shared event aligns actors that normally act at different times, compressing
ordinary work into a narrow interval. Reconnection, lease renewal, cache
expiration, restart, and reconciliation can all synchronize work.

Synchronization is not merely a traffic surge. Evidence must connect the surge
to a common phase-aligning event.

## Supporting properties

Use these as qualifiers, not as additional core curves:

- **Boundary crossing:** failure moves across an intended isolation domain.
- **Containment breach:** a boundary expected to hold does not.
- **Control-plane/data-plane coupling:** one plane impairs or depends on the
  other in a consequential way.
- **Shared-resource spillover:** independent workloads contend for a common
  pool, quota, or budget.
- **Asymmetric impact:** populations, platforms, operations, or regions
  experience materially different depth or duration.
- **Propagation front:** a change reaches cohorts progressively through a fleet
  or topology.

## Classification rules

1. Name the observable before naming its curve.
2. Do not infer mechanism from curve alone.
3. Permit multiple mechanisms and stage transitions.
4. Preserve unknowns and competing interpretations.
5. Treat classifications as revisable hypotheses.
6. Prefer the smallest vocabulary that explains the evidence.

## Example

For the 2019 Cloudflare WAF outage:

```text
Observable: Failed or unserved HTTP requests
Curve: Cliff
Causal geometry: Global control-plane fan-out
Amplification: Pathological CPU cost in a mandatory request path
Supporting property: Weak rollout containment
Recovery: Sharp recovery after global WAF termination
```

Calling the event a "fan-out shape" loses an important distinction: the cliff
is observed in requests, while fan-out describes how the rule reached the
fleet.
