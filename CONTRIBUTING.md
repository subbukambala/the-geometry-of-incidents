# Contributing

Contributions must improve the evidence record, sharpen a definition, add a
counterexample, or turn an observation into a testable engineering control.

## Before opening a change

- Read the [framework](docs/framework.md),
  [vocabulary](docs/vocabulary.md), and [limitations](docs/limitations.md).
- Search existing issues for the incident, term, or proposed change.
- For a taxonomy change, provide at least two examples and one counterexample.

## Add or revise a case study

1. Prefer the operator's public incident report as the primary source.
2. Name the plotted observable, units, population, and aggregation when known.
3. Separate **reported facts** from **project interpretation**.
4. Complete all six TRACER fields. Mark unknown evidence as unknown.
5. Name the user-impact curve separately from causal geometries.
6. Record competing interpretations and confidence.
7. Link every proposed control to an observed propagation, amplification,
   containment, or recovery property.

Use [`templates/tracer-review-template.md`](templates/tracer-review-template.md)
for prose and [`templates/incident-coding-template.csv`](templates/incident-coding-template.csv)
for the corpus row.

## Evidence standard

- Cite material factual claims directly.
- Prefer primary operator reports, status histories, technical RCAs, and
  first-party recovery guidance.
- Do not infer missing metrics from charts unless the method is documented.
- Label geometric classifications as interpretation.
- Preserve disagreement instead of forcing consensus.

## Style

- Use precise, plain language.
- Avoid blame and hindsight certainty.
- Do not call a curve a cause.
- Do not treat a single incident as proof of a general rule.
- Use absolute dates and identify time zones.

## Review expectations

A case-study pull request should include a source check, link check, and a
second-person classification review when possible. By contributing, you agree
that your contribution is available under the repository's CC BY 4.0 license.
