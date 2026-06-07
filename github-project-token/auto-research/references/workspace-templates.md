# Workspace Templates

Use these templates when initializing or repairing an auto-research workspace. Adapt field names only when the project already has a stronger local convention.

## research-state.yaml

```yaml
project:
  title: ""
  field: ""
  one_sentence_goal: ""
  target_venue_class: ""
  constraints:
    compute: ""
    data: ""
    deadline: ""
    budget: ""

current_question: ""
current_direction: "bootstrap"
last_updated: ""

hypotheses:
  - id: "H001"
    title: ""
    status: "proposed"
    mechanism: ""
    prediction: ""
    metric: ""
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

## Current Claim

State the strongest supportable claim in one paragraph.

## What We Know

- 

## Evidence

| Experiment | Hypothesis | Result | Interpretation | Confidence |
|---|---|---|---|---|

## Mechanisms

Explain why results may be happening.

## Negative Results

Record what has been ruled out and why it matters.

## Open Questions

- 

## Paper Backbone

Abstract draft:

Introduction argument:

Core contribution:

Key figures:
```

## protocol.md

```markdown
# Protocol: H001 Short Title

Hypothesis:

Mechanism:

Prediction:

Metric:

Baseline:

Minimum experiment:

Controls:

Sanity checks:

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

## Current Best Result

## What Changed

## Evidence

## What We Learned

## Risks

## Next
```
