# Auto Research

Auto Research is a Codex Skill for turning a research idea into a rigorous, agent-assisted research workflow.

It is designed for researchers who want to use coding agents as long-horizon research collaborators: the human provides the idea, taste, constraints, and final judgment; the agent helps with literature review, hypothesis generation, experiment planning, implementation, evaluation, synthesis, and paper-ready writing.

## Motivation

Coding agents are making research ability more widely accessible. A motivated student or independent researcher can now use tools like Codex and Claude Code to search, implement, test, and iterate at a pace that previously required a much larger engineering setup.

Auto Research tries to turn that shift into a reusable workflow:

- Start from an idea instead of a fully specified project.
- Brainstorm with an AI agent to sharpen the research question.
- Convert vague intuitions into falsifiable hypotheses.
- Run small, evidence-driven experiments.
- Maintain research memory across sessions.
- Synthesize results into a paper-ready narrative.

The goal is not to replace researchers. The goal is to amplify willingness, taste, execution, and access to technical tools.

## What This Skill Does

Auto Research helps an AI coding agent:

- Bootstrap a research workspace from a raw idea.
- Search and summarize related work.
- Generate mechanistic, testable hypotheses.
- Design minimum credible experiments.
- Separate confirmatory results from exploratory observations.
- Track experimental protocols, results, and decisions.
- Update a living research narrative in `findings.md`.
- Produce progress reports and paper-ready outlines.

## Repository Structure

```text
auto-research/
  SKILL.md
  agents/
    openai.yaml
  references/
    workspace-templates.md
```

`SKILL.md` contains the core instructions loaded by Codex when the skill is used.

`references/workspace-templates.md` contains reusable templates for research state, experiment protocols, analysis notes, and progress reports.

## Installation

Clone this repository:

```powershell
git clone https://github.com/scienceliuc/auto-research.git
cd auto-research
```

Copy the skill folder into your Codex skills directory:

```powershell
Copy-Item -Recurse .\auto-research "$env:USERPROFILE\.codex\skills\auto-research"
```

If you use a custom `CODEX_HOME`, copy it there instead:

```powershell
Copy-Item -Recurse .\auto-research "$env:CODEX_HOME\skills\auto-research"
```

## Usage

Invoke the skill in Codex:

```text
Use $auto-research to turn this idea into an autonomous research plan:
I want to study whether coding agents can improve the research productivity of non-CS students.
```

Example prompts:

```text
Use $auto-research to bootstrap a research workspace for my idea.
```

```text
Use $auto-research to convert this research direction into hypotheses, experiments, and a paper outline.
```

```text
Use $auto-research to review my current findings.md and decide whether to deepen, broaden, pivot, or conclude.
```

## Workflow

Auto Research follows a two-loop process.

### Bootstrap

1. Clarify the research question.
2. Search related work.
3. Identify the gap.
4. Generate hypotheses.
5. Choose the first experiment by expected information gain.

### Inner Loop

1. Write an experiment protocol before running code.
2. Run the smallest credible test.
3. Record raw results and commands.
4. Analyze outcomes and caveats.
5. Update research state and findings.

### Outer Loop

1. Review results across experiments.
2. Identify mechanisms behind successes and failures.
3. Revisit literature when needed.
4. Decide whether to deepen, broaden, pivot, or conclude.
5. Produce progress artifacts for human review.

## Research Workspace Created By The Skill

When used in a research project, the skill creates or maintains a structure like this:

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

This gives the agent durable memory across sessions and gives the researcher a clean audit trail of decisions, experiments, and claims.

## Research Discipline

Auto Research emphasizes:

- Literature-grounded novelty.
- Mechanistic hypotheses.
- Small experiments with clear metrics.
- Baseline and sanity checks.
- Explicit negative results.
- Citation verification.
- Clear separation between evidence and speculation.

## Status

This project is an early-stage research automation skill. The current version focuses on workflow design, research memory, and agent instructions. Future versions may add scripts for workspace initialization, literature ingestion, experiment dashboards, and report generation.

## License

Add a license before broad public reuse.
