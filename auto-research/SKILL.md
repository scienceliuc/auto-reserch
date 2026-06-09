---
name: auto-research
description: Turns an AI research idea into a top-conference-oriented autonomous research workflow for coding agents. Use when a user wants to brainstorm publishable AI research, target venues such as NeurIPS/ICML/ICLR/ACL/AAAI/COLM, build literature-grounded hypotheses, run rigorous experiments, maintain research memory, simulate reviewers, synthesize findings, or prepare a paper-ready research repository.
---

# Auto Research

Autonomous AI research workflow for coding agents. Convert a raw idea into a venue-targeted, evidence-backed, paper-ready research project.

The goal is not "run many experiments." The goal is to discover and defend a clear contribution that can survive top AI conference review.

## Operating Principle

Optimize for compounding research judgment.

The human supplies vision, taste, constraints, and final scientific judgment. The agent supplies persistence: literature search, hypothesis formation, implementation, measurement, result synthesis, paper scaffolding, and reviewer-style critique.

Move autonomously on routine work. Ask the human only for high-level taste decisions, expensive compute, private data use, risky pivots, or final claim approval.

## Success Definition

A project is paper-ready only when it has:

- A one-sentence contribution with clear "what / why / so what."
- Verified novelty against the closest related work.
- Claims that are falsifiable and matched to evidence.
- Strong, recent, fairly tuned baselines.
- Ablations that isolate the mechanism.
- Multiple runs or uncertainty reporting when quantitative claims depend on variance.
- Clear limitations and failure cases.
- A Figure 1 or main result figure that explains the idea quickly.
- Verified citations, not citations generated from memory.
- A reviewer simulation with concrete weaknesses and fixes.

For detailed top-venue gates, read `references/top-venue-workflow.md`.

## First Response

Classify the user's starting point:

- **Raw idea**: ask 1-3 concise questions about field, target venue class, available compute/data, and intended contribution.
- **Research question**: restate it as a falsifiable claim, identify assumptions, then bootstrap the workspace.
- **Existing repo or notes**: inspect files first, preserve user work, and add research state around the existing project.
- **Ongoing project**: read `research-state.yaml`, `findings.md`, `paper/story.md`, `research-log.md`, and latest experiment folders before acting.

If the user says "start", "继续", "帮我推进", or gives enough context, proceed instead of interviewing.

## Workspace

Create or maintain this structure at the project root:

```text
research-state.yaml
research-log.md
findings.md
literature/
  survey.md
  novelty-ledger.md
experiments/
  H001-short-slug/
    protocol.md
    code/
    results/
    analysis.md
src/
data/
figures/
paper/
  story.md
  claims.md
  outline.md
  related-work.md
  reviewer-simulation.md
to_human/
```

For starter templates, read `references/workspace-templates.md`.

Rules:

- Treat `research-state.yaml` as machine-readable project memory.
- Treat `findings.md` as the evolving scientific narrative, not a log dump.
- Treat `paper/story.md` as the top-conference story spine.
- Treat `paper/claims.md` as the claim-evidence contract.
- Treat `literature/novelty-ledger.md` as the anti-incrementalism defense.
- Put reusable implementation in `src/`; do not copy helpers into each experiment.
- Record raw metrics, logs, seeds, configs, and commands before writing conclusions.

## Workflow

Run five phases. Loop backward whenever evidence changes the story.

### Phase 1: Venue and Problem Framing

1. Identify likely venue family: NeurIPS/ICML/ICLR for general ML, ACL/EMNLP for NLP, AAAI/IJCAI for broader AI, COLM for language models, or systems venues when the core contribution is infrastructure.
2. Write the two-sentence pitch:
   - Problem: what community pain or scientific gap matters?
   - Insight: what mechanism, principle, or capability changes the situation?
3. Define the intended contribution type:
   - New method
   - New benchmark or evaluation
   - Mechanistic explanation
   - Negative result or failure analysis
   - Systems/tooling contribution
   - Theory or formalization
4. Create initial `paper/story.md` with "what / why / so what."

### Phase 2: Literature and Novelty

1. Search broadly, then narrowly. Use arXiv, Semantic Scholar, Crossref, official venue proceedings, benchmark leaderboards, project pages, and GitHub repos when tools/network permit.
2. For each important paper, record claim, method, evidence, limitation, and why it is close.
3. Maintain `literature/novelty-ledger.md` with the closest related work and the exact difference.
4. Kill or reframe ideas that are only "X plus small engineering" unless the simplicity or failure analysis itself is the contribution.
5. Before experiments scale up, write the strongest anticipated reviewer novelty objection and a planned answer.

### Phase 3: Hypothesis and Evidence Plan

Generate 3-7 hypotheses. Each hypothesis must include:

- Mechanism: why the effect should happen.
- Prediction: what should change if the hypothesis is right.
- Falsification: what result would make the hypothesis weaker.
- Minimum experiment: smallest credible test.
- Baseline: strongest practical comparison.
- Ablation: component or condition that should remove the effect.
- Metric: why this metric matches the claim.
- Cost: compute, data, time, and risk.

Choose the next experiment by expected information gain per cost, not by ease alone.

### Phase 4: Experiment Loop

For each experiment:

1. Write `experiments/{hypothesis}/protocol.md` before running code.
2. Mark the experiment as `confirmatory` if it tests a pre-written protocol; otherwise mark it `exploratory`.
3. Implement the smallest credible version.
4. Run sanity checks before trusting metrics: sample inspection, split integrity, baseline parity, NaN/Inf checks, deterministic seeds where practical, and leakage checks.
5. Save commands, configs, raw outputs, plots, and environment details.
6. Write `analysis.md` with result, interpretation, caveats, and next action.
7. Update `research-state.yaml`, `research-log.md`, `findings.md`, and `paper/claims.md`.

Negative results are progress when they rule out a plausible mechanism. Record what belief changed.

### Phase 5: Paper and Reviewer Loop

After every meaningful result:

1. Update `paper/story.md`: does the story still hold?
2. Update `paper/claims.md`: which claims are supported, weakened, or untested?
3. Draft or revise the key figure plan.
4. Simulate top-conference reviewers using Quality, Clarity, Significance, and Originality.
5. Convert each simulated weakness into either an experiment, a clarification, a limitation, or a scoped-down claim.
6. When evidence is strong enough, route to `ml-paper-writing` for full drafting and citation discipline.

Do not wait until the end to think about the paper. The paper is the steering wheel.

## Top-Venue Quality Gates

Before declaring a project mature, pass these gates:

- **Novelty gate**: the closest 5-10 papers are summarized and the contribution difference is explicit.
- **Claim gate**: every central claim has matching evidence and falsification criteria.
- **Baseline gate**: comparisons are fair, recent, and tuned within practical constraints.
- **Ablation gate**: the key mechanism is isolated from surrounding engineering.
- **Robustness gate**: results are checked across seeds, datasets, model sizes, tasks, or conditions where feasible.
- **Reproducibility gate**: another expert could rerun the main result from the repo.
- **Reviewer gate**: likely reject reasons are written before submission and addressed where possible.
- **Citation gate**: citations are verified through real sources; unverified citations are marked.

If any gate fails, do not hide the weakness. Either fix it, scope the claim down, or turn the weakness into a clear limitation.

## Human Collaboration

Use the human for:

- Choosing among high-level directions.
- Judging taste, novelty, and venue fit.
- Deciding whether a result is exciting enough to deepen.
- Approving paid compute, private data, or irreversible actions.
- Reviewing final claims before public submission.

Do not block on the human for:

- Creating project scaffolding.
- Reading and summarizing papers.
- Writing experiment protocols.
- Running small local experiments.
- Fixing routine implementation errors.
- Updating memory files and paper scaffolds.

## Skill Routing

Use specialized skills when they fit:

- `brainstorming-research-ideas` for divergent and convergent idea generation.
- `creative-thinking-for-research` for unusual angles, analogy, inversion, and constraint manipulation.
- `academic-paper-review` to critique a candidate paper or your own draft.
- `ml-paper-writing` for NeurIPS/ICML/ICLR/ACL/AAAI/COLM drafting, templates, reviewer criteria, and citation verification.
- `academic-plotting` or `nature-figure` for paper-quality figures.
- Domain training/evaluation skills for implementation, fine-tuning, benchmarking, serving, or interpretability.

If no domain skill fits, implement the smallest reliable workflow directly and document assumptions.

## Failure Modes

If progress stalls:

- Stop random experiments.
- Re-read `findings.md`, `paper/story.md`, and recent `analysis.md`.
- Check whether the metric actually measures the claim.
- Search for related failures and stronger baselines.
- Shrink the experiment until the mechanism can be observed.
- Pivot only after recording what the current direction ruled out.

If results look too good:

- Re-run from a clean state.
- Check leakage, split contamination, prompt contamination, evaluation scripts, and baseline parity.
- Add an ablation that should destroy the effect.
- Mark claims provisional until reproduced.

If the story feels weak:

- Rewrite the one-sentence contribution.
- Identify the nearest paper that makes the result look incremental.
- Add the missing experiment, scope down the claim, or pivot to the sharper finding.
