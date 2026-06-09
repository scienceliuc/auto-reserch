# Top-Venue Workflow

Use this reference when the user wants the project to target NeurIPS, ICML, ICLR, ACL, AAAI, COLM, or comparable AI venues. Check the official call for papers before final submission because page limits and required statements change.

## Acceptance Model

Top AI conference reviewers usually evaluate four dimensions:

| Dimension | Reviewer question | Project artifact |
|---|---|---|
| Quality | Are the claims technically sound and well-supported? | `paper/claims.md`, experiment analyses |
| Clarity | Can reviewers understand and reproduce the work? | `paper/story.md`, README, methods notes |
| Significance | Does the result matter to the community? | problem framing, Figure 1, main result |
| Originality | What is new compared with close prior work? | `literature/novelty-ledger.md` |

Treat the project as weak if any dimension is below the venue bar.

## Contribution Archetypes

Choose one primary archetype. Mixed contributions are allowed, but the paper still needs one central story.

| Archetype | What must be proven | Required evidence |
|---|---|---|
| New method | The method improves a meaningful objective for a non-obvious reason | strong baselines, ablations, robustness |
| New benchmark | The benchmark exposes a real missing capability | task validity, human or expert checks, baseline spread |
| Mechanistic analysis | The work explains why a phenomenon happens | causal tests, interventions, falsifiable predictions |
| Negative result | A plausible belief fails under fair testing | strong setup, careful controls, useful diagnosis |
| Systems/tooling | The system enables new research or practice | scale, reliability, usability, comparison to alternatives |
| Theory/formalization | The formal result changes understanding or guarantees | assumptions, proofs, examples, limits |

## Two-Sentence Pitch

Use this before major experiments:

```text
[Community] currently cannot [important capability] because [specific bottleneck or false assumption].
We show that [core insight/method] enables [result], because [mechanism], supported by [key evidence].
```

If this pitch cannot be written clearly, the project is not ready for large experiments.

## Novelty Ledger

For each close paper, record:

- What it claims.
- What evidence it gives.
- What assumption or limitation it leaves open.
- Whether your work is different in problem, mechanism, evidence, scale, or interpretation.
- The strongest reviewer argument that your work is incremental.

Strong novelty statements are precise:

```text
Prior work shows X under setting A. We show Y under setting B, and the difference matters because Z.
```

Weak novelty statements are vague:

```text
No one has applied this exact combination before.
```

## Experiment Matrix

Plan experiments by claim, not by convenience.

| Experiment type | Purpose | Minimum standard |
|---|---|---|
| Main result | Support the central claim | strong baseline, same evaluation budget |
| Ablation | Isolate the mechanism | remove or replace one key component |
| Robustness | Test scope | vary seed, dataset, model, task, scale, or prompt |
| Failure case | Calibrate limits | show where method does not work |
| Efficiency | Support cost claims | report wall time, hardware, memory, and throughput |
| Qualitative | Explain behavior | representative examples, not cherry-picked only |

## Claim-Evidence Contract

Every central claim needs this record:

```text
Claim:
Scope:
Evidence:
Falsification:
Closest alternative explanation:
Experiment that rules out the alternative:
Current confidence:
```

Do not make claims broader than the evidence. Scope-down beats overclaiming.

## Baseline Standard

For comparative AI papers:

- Include the strongest practical recent baseline, not only an easy baseline.
- Use official implementations when possible.
- Tune baselines enough that reviewers cannot call them strawmen.
- Match compute, data, prompt budget, and evaluation protocol where feasible.
- Report when a baseline could not be run and why.

If the strongest baseline is too expensive, run a smaller controlled comparison and state the limitation explicitly.

## Ablation Standard

Ablations should answer "why did this work?"

Good ablations:

- Remove the claimed mechanism.
- Replace it with a simpler alternative.
- Test sensitivity to the most important hyperparameters.
- Distinguish the proposed explanation from at least one alternative explanation.

Weak ablations:

- Remove components that are not part of the main claim.
- Only show every component helps a little.
- Do not connect back to a mechanism.

## Reviewer Simulation

Run reviewer simulation before paper drafting and again before submission.

Use these personas:

1. **Skeptical novelty reviewer**: "Is this just a straightforward extension?"
2. **Methodology reviewer**: "Are baselines, ablations, and statistics adequate?"
3. **Clarity reviewer**: "Can I understand the paper without reading code?"
4. **Significance reviewer**: "Why should this community care?"
5. **Reproducibility reviewer**: "Can I rerun the key result?"

For each persona, write:

- Likely score or recommendation.
- Top 3 concerns.
- Evidence that would change the score.
- Revision or experiment needed.

## Paper Story Gate

Before drafting a full paper, confirm:

- The abstract can be written in 5 sentences.
- Figure 1 communicates the core idea or result without the main text.
- The introduction reaches contributions quickly.
- The method section can be reimplemented by an expert.
- The experiments section maps each result to a claim.
- Related work is organized by ideas, not by paper summaries.
- Limitations are honest and do not undermine the central claim.

## Citation Discipline

Never generate BibTeX from memory.

For every citation:

1. Search a real source.
2. Verify the paper exists.
3. Verify the cited claim appears in the paper.
4. Retrieve BibTeX from DOI, arXiv, ACL Anthology, OpenReview, or the official source.
5. Mark uncertain citations as placeholders requiring human verification.

## Decision Rules

**Deepen** when a result is real but reviewers will ask for mechanism or robustness.

**Broaden** when the story is strong but scope is too narrow for the target venue.

**Pivot** when the original contribution is incremental but a sharper finding emerged.

**Conclude** when the claim-evidence contract is strong enough that a skeptical reviewer would need a specific, fixable objection rather than a general doubt.
