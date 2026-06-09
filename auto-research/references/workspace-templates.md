# Workspace Templates

Use these templates when initializing or repairing an auto-research workspace. Adapt field names only when the project already has a stronger local convention.

## research-state.yaml

```yaml
project:
  title: ""
  field: ""
  one_sentence_goal: ""
  target_venue_class: "NeurIPS|ICML|ICLR|ACL|AAAI|COLM|other"
  contribution_type: "method|benchmark|analysis|negative-result|systems|theory"
  constraints:
    compute: ""
    data: ""
    deadline: ""
    budget: ""

current_question: ""
current_direction: "bootstrap"
last_updated: ""

venue_strategy:
  primary_venue: ""
  backup_venues: []
  page_limit_notes: ""
  reviewer_expectations:
    quality: ""
    clarity: ""
    significance: ""
    originality: ""

story:
  two_sentence_pitch: ""
  what: ""
  why: ""
  so_what: ""
  figure1_plan: ""

hypotheses:
  - id: "H001"
    title: ""
    status: "proposed"
    mechanism: ""
    prediction: ""
    falsification: ""
    metric: ""
    baseline: ""
    ablation: ""
    minimum_experiment: ""
    expected_failure_mode: ""
    cost_estimate: ""

experiments:
  - id: "E001"
    hypothesis_id: "H001"
    status: "planned"
    type: "confirmatory"
    protocol_path: "experiments/H001-short-slug/protocol.md"
    results_path: ""
    headline_result: ""
    claim_ids: []

quality_gates:
  novelty: "not-started"
  claims: "not-started"
  baselines: "not-started"
  ablations: "not-started"
  robustness: "not-started"
  reproducibility: "not-started"
  reviewer_simulation: "not-started"
  citation_verification: "not-started"

decisions:
  next_action: ""
  open_questions: []
  risks: []
```

## research-log.md

```markdown
# Research Log

## YYYY-MM-DD HH:MM

Decision:

Evidence:

Rationale:

Next action:
```

## findings.md

```markdown
# Findings

## Current Contribution Claim

State the strongest supportable claim in one paragraph.

## One-Sentence Paper Story

What did we learn that the community did not already know?

## What We Know

- 

## Evidence

| Claim | Experiment | Result | Interpretation | Confidence |
|---|---|---|---|---|

## Mechanisms

Explain why results may be happening.

## Baselines and Ablations

Summarize whether comparisons are fair and which components matter.

## Negative Results

Record what has been ruled out and why it matters.

## Open Questions

- 

## Paper Backbone

Abstract draft:

Introduction argument:

Core contribution:

Key figures:

Closest related work:

Likely reviewer objection:
```

## literature/novelty-ledger.md

```markdown
# Novelty Ledger

## Working Contribution

One-sentence claim:

## Closest Related Work

| Paper | What it claims | Evidence | How our work differs | Risk level |
|---|---|---|---|---|

## Novelty Objections

1. Objection:
   Response:
   Needed evidence:

## Missing Citations

- [ ] 
```

## paper/story.md

```markdown
# Paper Story

## Target Venue

Primary:
Backup:

## Two-Sentence Pitch

Problem:

Insight:

## What / Why / So What

What:

Why:

So what:

## Contribution List

1. 
2. 
3. 

## Figure 1 Plan

Message:

Panels:

Evidence source:

## Paper Skeleton

Abstract:

Introduction arc:

Method:

Experiments:

Limitations:
```

## paper/claims.md

```markdown
# Claims

| ID | Claim | Status | Evidence | Falsification | Scope |
|---|---|---|---|---|
| C001 |  | proposed |  |  |  |

## Unsupported or Risky Claims

- 
```

## protocol.md

```markdown
# Protocol: H001 Short Title

Hypothesis:

Mechanism:

Prediction:

Falsification:

Metric:

Baseline:

Ablation:

Minimum experiment:

Controls:

Sanity checks:

Seeds / variance plan:

Compute/data cost:

What would support the hypothesis:

What would refute the hypothesis:

Pre-run notes:
```

## analysis.md

```markdown
# Analysis: E001

Protocol:

Commands:

Environment:

Raw outputs:

Primary metric:

Baseline comparison:

Ablation result:

Variance / uncertainty:

Sanity checks:

Interpretation:

Caveats:

Confirmatory vs exploratory:

Next action:
```

## to_human/progress-report.md

```markdown
# Progress Report

## Research Question

## Why It Matters

## Current Paper Story

## Current Best Result

## What Changed

## Evidence

## What We Learned

## Reviewer Risks

## Risks

## Next
```

## paper/reviewer-simulation.md

```markdown
# Reviewer Simulation

## Summary

Likely recommendation:

Confidence:

## Quality

Strengths:

Weaknesses:

Fixes:

## Clarity

Strengths:

Weaknesses:

Fixes:

## Significance

Strengths:

Weaknesses:

Fixes:

## Originality

Strengths:

Weaknesses:

Fixes:

## Top Reject Reasons

1. 
2. 
3. 

## Action Plan

- [ ] 
```
