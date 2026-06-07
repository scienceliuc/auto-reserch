---
name: auto-research
description: Turns a research idea into a rigorous autonomous research workflow for AI coding agents. Use when a user wants to brainstorm research directions, convert an idea into hypotheses, run literature-grounded experiments, maintain research state, synthesize findings, prepare top-conference or journal submissions, or build an auto-research GitHub project/skill.
---

# Auto Research

Autonomous research for coding agents. Help the user move from idea to publishable evidence by combining human taste and direction with agentic literature review, hypothesis design, experiment execution, result synthesis, and paper preparation.

Use the user's idea as the seed, but do not treat the first phrasing as final. Turn it into a falsifiable research program.

## Operating Principle

Optimize for research compounding, not isolated task completion.

The human provides vision, taste, constraints, and final judgment. The agent supplies persistence, search, implementation, measurement, documentation, and synthesis. Keep the human in the loop for scientific taste and risky strategic pivots, but do not ask for approval on routine execution.

## First Response

Classify the user's starting point:

- **Raw idea**: clarify the target field, desired contribution, and available resources in 1-3 concise questions.
- **Research question**: restate it as a testable claim, identify assumptions, then bootstrap the workspace.
- **Existing repo or notes**: inspect files first, preserve user work, then add auto-research state around the existing project.
- **Ongoing project**: read `research-state.yaml`, `findings.md`, `research-log.md`, and latest experiment folders before acting.

If the user asks to "start" or gives enough context, proceed instead of over-interviewing.

## Workspace

Create or maintain this structure at the project root:

```text
research-state.yaml
research-log.md
findings.md
literature/
experiments/
  H001-short-slug/
    protocol.md
    code/
    results/
    analysis.md
src/
data/
to_human/
paper/
```

For exact starter templates, read `references/workspace-templates.md`.

Rules:

- Keep `research-state.yaml` as the machine-readable source of current direction, hypotheses, experiments, and next actions.
- Keep `findings.md` as the evolving paper backbone, not a dump of logs.
- Keep `research-log.md` as a chronological decision trail.
- Save literature notes in `literature/`, one paper per file plus a running `literature/survey.md`.
- Put reusable code in `src/`; do not duplicate helpers across experiment folders.
- Put raw metrics, logs, small result tables, and plot data in `data/` or each experiment's `results/`.

## Research Loop

Run a two-loop process.

### Bootstrap

1. Translate the idea into a research question, scope, and intended venue class.
2. Search literature from multiple sources when network/tools permit: arXiv, Semantic Scholar, Crossref, official project pages, benchmark leaderboards, and related GitHub repos.
3. Summarize each relevant paper with claim, method, evidence, limitation, and relevance.
4. Identify the gap: what is unresolved, under-tested, newly possible, or wrongly assumed.
5. Generate 3-7 hypotheses. Each hypothesis must include mechanism, prediction, minimum experiment, metric, expected failure mode, and cost.
6. Choose the first hypothesis by expected information gain per unit cost.

### Inner Loop

For each experiment:

1. Write `experiments/{hypothesis}/protocol.md` before running code.
2. Mark the experiment as confirmatory if it tests the protocol directly; mark it exploratory if the idea emerged during execution.
3. Implement the smallest credible test.
4. Run sanity checks before trusting metrics: data samples, baseline reproduction, deterministic seeds where practical, NaN/Inf checks, and obvious leakage checks.
5. Record raw results and commands.
6. Write `analysis.md` with outcome, interpretation, caveats, and next action.
7. Update `research-state.yaml`, `research-log.md`, and `findings.md`.

Negative results are useful when they rule out a plausible mechanism. Document what changed in the agent's beliefs.

### Outer Loop

After several experiments, a surprising result, or a stall:

1. Cluster results by mechanism, not by filename.
2. Ask what explains successes and failures.
3. Revisit literature if assumptions are broken or results are hard to interpret.
4. Decide one direction:
   - **Deepen**: a supported result needs ablations, mechanism tests, or robustness checks.
   - **Broaden**: the contribution is promising but needs adjacent coverage.
   - **Pivot**: the original premise is weaker than a discovered opportunity.
   - **Conclude**: evidence is sufficient for a coherent paper story.
5. Produce a short progress artifact in `to_human/` when there is a meaningful update.

## Quality Bar

Enforce these standards:

- Prefer mechanistic hypotheses over blind metric chasing.
- Lock the metric and baseline before evaluating a claimed improvement.
- Separate confirmatory evidence from exploratory observations.
- Compare against the strongest practical baseline available under the user's compute constraints.
- Track compute, data, prompts, seeds, dependencies, and commit hashes when relevant.
- Treat benchmark gains without ablations as provisional.
- Treat generated text, citations, and paper claims as untrusted until verified.
- Do not invent citations. If a citation cannot be verified, mark it as needing verification.

## Human Collaboration

Use the human for:

- Choosing between high-level research directions.
- Judging taste, novelty, and venue fit.
- Approving expensive compute, paid services, private data use, or irreversible actions.
- Reviewing final claims before submission.

Do not block on the human for:

- Creating project scaffolding.
- Running small local experiments.
- Reading papers and writing summaries.
- Fixing routine implementation errors.
- Updating research memory files.

## Outputs

Depending on the user's request, produce one or more:

- Research plan with hypotheses and experiments.
- Initialized auto-research workspace.
- Literature survey with verified links.
- Experiment protocols and runnable code.
- Results tables, plots, and analysis notes.
- `findings.md` narrative that can become an abstract/introduction.
- Progress report in Markdown, HTML, PDF, or slides.
- Paper draft with citation verification notes.

## Tool and Skill Routing

Use specialized skills when they fit:

- Literature and citation workflows: `nature-academic-search`, `academic-paper-review`, or `ml-paper-writing`.
- Brainstorming: `brainstorming-research-ideas` or `creative-thinking-for-research`.
- Training and evaluation: relevant ML training, fine-tuning, evaluation, or inference skills.
- Figures: `academic-plotting` or `nature-figure`.
- Papers, responses, and presentations: writing or presentation skills matching the target venue.

If no domain skill exists, implement the smallest reliable workflow directly and document assumptions.

## Failure Modes

If progress stalls:

- Stop random trial-and-error.
- Re-read `findings.md` and recent `analysis.md` files.
- Check whether the metric is measuring the real objective.
- Search for related failures in papers and issues.
- Shrink the experiment until the core mechanism can be observed.
- Pivot only after recording what the current path ruled out.

If results look too good:

- Re-run from a clean state.
- Check leakage, split contamination, evaluation scripts, and baseline parity.
- Add an ablation that should remove the effect.
- Mark claims provisional until reproduced.
