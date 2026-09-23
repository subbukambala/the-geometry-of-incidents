# Incident Corpus Data Dictionary

The starter corpus exists to exercise the schema. Four selected incidents are
not a representative sample and cannot support prevalence claims.

## General rules

- One row represents one incident-level interpretation for one primary
  observable.
- Use additional rows when materially different observables require separate
  coding.
- Use semicolons for multiple values inside one CSV cell.
- Leave unsupported values blank; do not invent estimates.
- `reported facts` and `classification` have different evidence status.

## Fields

| Field | Meaning |
| --- | --- |
| `incident_id` | Stable lowercase identifier, normally operator and year |
| `operator` | Organization operating the affected service or product |
| `incident_date` | Incident start date in ISO 8601 format |
| `title` | Short identifying title |
| `primary_source_url` | Operator report or equivalent first-party source |
| `observable` | Explicit y-axis concept used for curve classification |
| `observable_unit` | Requests, users, hosts, tenants, workflows, or other unit |
| `population` | Denominator or scoped population represented |
| `aggregation` | Global, regional, tenant-specific, percentile, bucket size, or equivalent |
| `breadth` | Evidence-based description or measure of affected scope |
| `depth` | Evidence-based severity within the affected population |
| `duration` | Containment, primary restoration, and full-recovery intervals when known |
| `speed` | Time to initial or peak impact, or a qualitative value if only that is supported |
| `recovery` | Restoration behavior and milestones |
| `user_impact_curve` | One or more canonical observable curves |
| `causal_geometries` | Supported fan-out, cascade, feedback loop, or synchronization mechanisms |
| `origin` | Initial disturbance supported by evidence |
| `propagation` | Paths that carried the disturbance |
| `amplification` | Mechanisms that increased scale, depth, speed, or persistence |
| `impact_surface` | Exact users, operations, regions, or resources affected |
| `containment` | Boundaries that held, failed, or were missing |
| `recovery_path` | Sequence and mechanism of restoration |
| `supporting_properties` | Boundary, coupling, spillover, asymmetry, or front qualifiers |
| `competing_interpretation` | Plausible alternate reading or unresolved ambiguity |
| `evidence_status` | Source types available for the coded facts |
| `confidence` | `low`, `medium`, `medium-high`, or `high` with reviewer justification |
| `reviewer` | Reviewer identifier; blank in the starter corpus pending independent review |
| `framework_version` | Version used for classification |
| `notes` | Scope, provenance, or interpretation caveats |

## Confidence guidance

- **High:** primary evidence directly describes the mechanism and observable.
- **Medium-high:** mechanism is well supported, but curve or population is
  partly qualitative.
- **Medium:** material interpretation is required or evidence is incomplete.
- **Low:** classification is provisional and should not be used in aggregate
  findings.

Confidence is not a score of operator transparency or incident-review quality.
