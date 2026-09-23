# The Geometry of Incidents

**Working framework - version 0.1.0**

Incident geometry is a review technique for tracing a production failure from
its point of origin to user impact and recovery. The goal is to explain why the
impact took the shape it did, using the system's actual dependency paths,
rollout mechanisms, isolation boundaries, and recovery behavior.

> Incidents do not spread randomly. They follow the architecture.

The repository contains the working framework, review templates, four
source-backed case studies, and a starter corpus. Version 0.1.0 is practitioner
work. It has not been validated as a predictive taxonomy.

## Why I built this

Across hundreds of public postmortems, I kept seeing different root causes
produce familiar impact and recovery patterns. I built incident geometry to
connect those patterns to the architectural paths that carried and amplified
the failure, so a review can lead to a better design question rather than stop
at a timeline. The motivation and two early examples are described in my
[WeAreDevelopers article](https://www.wearedevelopers.com/magazine/764-the-geometry-of-incidents-connecting-user-impact-to-architecture).

## 1. What is incident geometry?

The review follows the failure through six stages:

```text
Origin -> Propagation -> Amplification -> Impact -> Containment -> Recovery
```

**TRACER** is the mnemonic used in the conference talk:

| TRACER | Formal term | Question |
| --- | --- | --- |
| Trigger | Origin | Where did the disturbance begin? |
| Route | Propagation | How did it travel? |
| Amplification | Amplification | What made it larger, faster, or persistent? |
| Consequence | Impact | Who or what experienced the failure? |
| Extent | Containment | What limited its extent, and which boundary failed? |
| Recovery | Recovery | How did the system return to health? |

The reviewer names one user-impact observable and describes its curve over
time. That curve is kept separate from the causal geometry. A global fan-out
may produce a cliff in failed requests; synchronized recovery may produce a
wave of repair work. Neither curve proves the mechanism by itself.

Read the [framework](docs/framework.md) and
[vocabulary](docs/vocabulary.md) for the complete model.

## 2. How is it different from a timeline or root-cause analysis?

Each method answers a different question:

| Method | Primary question |
| --- | --- |
| Timeline | What happened, and when? |
| Root-cause analysis | What initiated the failure, and why? |
| Blast radius | How much was affected? |
| Incident geometry | How did the architecture transform the initiating fault into this pattern of impact and recovery? |

Use it alongside the timeline and causal analysis. It adds the structural view:
the paths that carried failure, the mechanisms that enlarged it, the boundaries
that held or failed, and the work required to recover.

## 3. How do I apply it to one incident?

1. Name one user- or workload-visible observable and its units.
2. Establish reported facts from the timeline and primary evidence.
3. Walk through TRACER without forcing the incident into one label.
4. Name the observable's curve separately from causal mechanisms.
5. Identify the boundary that held, failed, or was missing.
6. Convert each finding into a control and a verification test.

Start with the [30-minute guide](docs/getting-started.md) and copy the
[TRACER review template](templates/tracer-review-template.md). Use the
[coding template](templates/incident-coding-template.csv) when comparing
multiple incidents.

## 4. Where can I see a complete example?

Start with the [CrowdStrike 2024 case study](case-studies/crowdstrike-2024.md).
Automated one-to-many distribution produced a cliff in affected Windows hosts;
host-by-host remediation produced the long recovery tail.

Additional cases:

- [Cloudflare WAF, 2019](case-studies/cloudflare-2019.md) - global fan-out and a sharp recovery
- [GitHub database failover, 2018](case-studies/github-2018.md) - cascade, divergent state, and backlog recovery
- [AWS DynamoDB US-EAST-1, 2025](case-studies/aws-dynamodb-2025.md) - fan-out, cascade, synchronized repair, and congestive collapse

## Repository map

- [`docs/`](docs/) - framework, vocabulary, adoption guide, and limitations
- [`templates/`](templates/) - reusable review and coding forms
- [`case-studies/`](case-studies/) - facts separated from project interpretation
- [`data/`](data/) - starter corpus and data dictionary
- [`figures/`](figures/) - reusable project-authored diagrams

## Evidence and interpretation

Factual claims in the case studies cite operator reports and other first-party
sources. Geometry labels are our interpretation, not the operators' wording.
When the public record does not support a metric, the field stays unknown.

See [limitations](docs/limitations.md) before applying the framework to research
or automated classification.

## Citation and license

Citation metadata is available in [`CITATION.cff`](CITATION.cff). Unless a file
states otherwise, this repository is licensed under the
[Creative Commons Attribution 4.0 International License](LICENSE).

Contributions are welcome through the process in
[`CONTRIBUTING.md`](CONTRIBUTING.md).
