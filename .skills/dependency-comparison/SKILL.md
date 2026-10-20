---
name: dependency-comparison
description: Compare and rank software dependencies when selecting a library, package, framework, or replacement for a project. Use project-specific criteria, current primary evidence, and explicit tradeoffs rather than search visibility or popularity alone.
---

# Dependency Comparison

Produce a decision the user can inspect: a ranked candidate set, evidence for each
criterion, and an explanation of why the recommendation fits this project.
Comparison alone does not authorize installation or migration.

## Frame the decision

Read relevant project manifests and constraints first. Establish the needed
capabilities, runtime/platform versions, deployment environment, expected scale,
team familiarity, maintenance horizon, and budget where relevant. State reasonable
assumptions; ask only when an unknown could materially change the selection.

Separate hard requirements from preferences. A known failure of a hard requirement
(for example, missing platform support) excludes a candidate regardless of score.
An unverified hard requirement makes eligibility provisional. Flag license
requirements for verification rather than claiming legal compatibility from memory.

Include the existing dependency and a standard-library/no-new-dependency option
when plausible. Discover candidates through ecosystem registries, official
integration docs, repository topics, and alternatives beyond the first search
results. Declare the search scope and shortlist rationale. Cover all user-named
candidates; list exclusions and reasons. Do not claim to have compared every
dependency in an open-ended ecosystem. For a large set, screen broadly, then
research the viable shortlist to comparable depth.

## Gather comparable evidence

Use current official documentation, registry metadata, source repositories,
release notes, issue/PR histories, and security advisories. Search results and
marketing claims are discovery leads, not proof. Record the assessment date,
package identity, repository, evaluated version, sources, and measurement window.
Distinguish package-specific facts from monorepo-wide statistics.

Use a common observation window (normally the past 12 months, with a recent
90-day view if useful). Note pagination, sampling, unavailable APIs, and other
limits. Keep bots separate from human contributors where possible. If live
research is unavailable, provide a provisional comparison and identify stale or
missing evidence; never invent counts or imply a current check occurred.

Evaluate the following dimensions. Retain raw observations alongside judgments;
adapt depth and relevance to the decision.

| Dimension | Useful evidence and interpretation |
| --- | --- |
| Functional fit and compatibility | Required features and edge cases; supported runtime/platform versions; integration with the existing stack; accessibility, internationalization, or offline support when applicable. |
| Maintenance and release health | Last stable release; stable releases per window and typical interval; meaningful fixes and maintenance activity; support/EOL policy. Separate prereleases and bot-only activity. Frequent updates are not automatically better; a stable, complete library can release rarely. |
| Adoption and ecosystem | Stars and their trend, downstream dependents, registry downloads, integrations, and relevant production use. Note inflated/bot/CI downloads and incomparable ecosystem counts. Visibility is supporting evidence, not a quality verdict. |
| Maturity and stability | First public release and current major-version age, production history, deprecations, breaking-change frequency, migration guides, and backward compatibility. Repo creation date alone does not establish product age or reliability. |
| Documentation and developer experience | Version-matched installation and quickstart; API coverage; realistic examples; error handling; troubleshooting; migration docs; types/tooling. Inspect whether a representative project task is actually explained rather than judging website polish. |
| Contributors and continuity | Total contributors plus active human contributors in the window; distinct reviewers/maintainers; concentration of recent work; governance, succession, and organizational/funding continuity. Lifetime contributor count alone hides dependence on one person. |
| Responsiveness | Sample comparable bugs and PRs, recording sample size and selection; time to substantive maintainer response and resolution; unresolved critical bugs. Include unresolved items to avoid reporting only fast closures. Raw open-issue count is not a verdict. |
| Security and supply chain | Advisories affecting the evaluated version, fixes and response history, security policy, provenance/signing where available, install scripts, dependency risks, and relevant OpenSSF Scorecard checks. Interpret exploitability and project exposure; zero known advisories or a high aggregate score does not prove safety. |
| Quality and reliability | Relevant automated tests and CI, regression history, known correctness limitations, and reproducible results for the intended workload. Coverage percentages and badges alone do not establish correctness. |
| Performance and footprint | Relevant latency/throughput, memory, bundle or binary size, startup/build costs, and transitive dependency count/weight. Prefer representative measurements; label vendor benchmarks and differing environments. |
| Integration and ownership cost | Setup and operating effort, upgrade burden, team learning, observability/debugging, portability, data/API lock-in, migration and exit cost, plus license or paid-feature constraints. Distinguish open-source library features from hosted/paid offerings. |

Choose representative spot checks proportional to uncertainty. A small isolated
proof of concept can resolve a decisive compatibility or performance question;
use existing permissions and do not execute untrusted installation scripts or
change the project's dependencies merely to produce a comparison.

## Rank without hiding uncertainty

Set weights and scoring anchors before scoring candidates. Explain changes to
weights using project priorities, never to favor a preferred candidate. Use this
starting profile when no project-specific preference is available:

| Criterion | Weight |
| --- | ---: |
| Functional fit and compatibility | 25 |
| Maintenance and release health | 12 |
| Adoption and ecosystem | 5 |
| Maturity and stability | 5 |
| Documentation and developer experience | 10 |
| Contributors and continuity | 8 |
| Responsiveness | 5 |
| Security and supply chain | 12 |
| Quality and reliability | 8 |
| Performance and footprint | 5 |
| Integration and ownership cost | 5 |

These weights are a local decision aid, not an industry standard. Avoid counting
the same signal repeatedly (for example stars as both adoption and reliability).
Score each applicable criterion from 0–5: 0 = demonstrated unacceptable result,
1 = major weakness, 2 = material limitations, 3 = adequate, 4 = strong, 5 = strong
and specifically demonstrated for this project's needs. Define more concrete
anchors where a criterion is decisive; do not mechanically translate raw counts
into scores across different ecosystems.

Mark missing evidence `unknown`, never zero or average. Remove genuinely
inapplicable criteria consistently across candidates and renormalize weights.
For incomplete evidence, show evidence coverage (sum of known weights / total
applicable weight). Report a conservative score interval by assigning unknowns
0 for the lower bound and 5 for the upper bound:

`score out of 100 = 100 × sum(weight × score / 5) / sum(applicable weights)`

Use the same denominator for both bounds; do not rank incomplete candidates by
an average of only their known scores. Label any ordering provisional when
missing evidence could change the winner. Keep excluded and provisional-eligibility
candidates separate from the eligible ranking.

Show raw metric comparisons and per-criterion scores, not only the aggregate.
Give evidence confidence separately from quality. Check whether plausible weight
changes or uncertain scores change the top choice; report a close result or
conditional recommendation instead of false precision. A score supports judgment
and cannot override a failed hard requirement.

## Deliver the decision

Keep the depth proportional to the choice, but include:

- Project constraints, assumptions, research date, scope, and exclusions.
- A candidate-by-criterion evidence table with units/windows and source links;
  split into smaller tables if needed for readability.
- Weights, per-criterion scores, ranked totals or intervals, evidence coverage,
  and decisive unknowns. Explain qualitative scoring briefly.
- A recommended option and runner-up, concrete tradeoffs, sensitivity of the
  ranking, and what evidence or project change would reverse the recommendation.

When the outcome is inconclusive, identify the smallest useful next check. Do
not install a winner unless implementation is part of the user's request.

## Method sources and provenance

Originally authored for chris-skills from Christopher's dependency-selection
requirements. The rubric and weights are local synthesis. For deeper evaluation,
consult [CHAOSS project health metrics](https://www.chaoss.community/starter-project-health-metrics-model/)
for release and contributor continuity signals, and
[OpenSSF Scorecard](https://github.com/ossf/scorecard#readme) for security practice
checks. Neither source's aggregate measures replace project-specific judgment.
