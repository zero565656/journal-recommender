# Scoring Rubric

Use this rubric for two separate tasks: estimating a submission strategy from the abstract, and scoring journal fit after evidence collection. Keep both judgments evidence-bound and disclose uncertainty.

## Baseline Submission Estimate

This is not a manuscript-quality verdict. It is a planning heuristic for challenge/target/safety tiers.

| Dimension | Weight | 5 | 3 | 1 |
|---|---:|---|---|---|
| Novelty signal | 40% | New method, theory, dataset, mechanism, or framework | Clear improvement over known work | Mainly applies known methods to a narrower case |
| Problem importance | 25% | Core field problem or broad scientific/clinical/engineering relevance | Meaningful subproblem | Narrow local case or limited audience |
| Evidence strength | 25% | Strong validation signals: large data, multiple baselines, ablation, SOTA, external validation, theory/proof as appropriate | Some validation but incomplete scale/detail | Weak or unclear validation in the abstract |
| Writing clarity | 10% | Clear contribution, methods, results, and significance | Understandable but missing some detail | Confusing, incomplete, or vague |

Suggested mapping:

| Weighted score | Strategy label | Tentative baseline |
|---:|---|---|
| 4.2-5.0 | strong | CAS 1 / field-leading target |
| 3.2-4.1 | upper-middle | CAS 2 |
| 2.2-3.1 | middle | CAS 3 |
| 1.0-2.1 | conservative | CAS 4 or broader-scope journals |

Use cautious language:

- Good: "基于摘要文本信号，建议先按 2 区基准制定投稿策略。"
- Bad: "这篇论文质量是 2 区水平。"

If the user supplies acceptance constraints, supervisor target, full manuscript details, or known novelty level, let those override the abstract-only estimate.

## Journal Fit Score

Score 0-5 per dimension. Use `未确认` when evidence is unavailable; do not give positive credit for unverified claims.

| Dimension | Weight | Evidence |
|---|---:|---|
| Scope fit | 30% | Official Aims & Scope or verified journal-topic field |
| Article type fit | 15% | Research/review/methodology fit, article mix if available |
| Audience fit | 10% | Journal readership and field community |
| Impact and tier | 20% | CAS/JCR tier, TOP/flagship status, IF with page version/date |
| Review practicality | 15% | Review time, acceptance difficulty, user deadline |
| OA/APC fit | 5% | OA model, APC amount, budget fit |
| Reputation/risk | 5% | Warning lists, publisher reputation, indexing consistency |

Scope-fit anchors:

- 5: Aims & Scope explicitly covers the manuscript's core topic and method/application context.
- 4: Core topic is covered; method/application fit is plausible.
- 3: Broad field matches but the exact subfield is not explicit.
- 1: Only a loose discipline match.
- 0: Clear mismatch; exclude unless the user asks to keep it.

When Aims & Scope is unavailable, cap scope fit at 3 even if other metadata looks promising.

## Challenge/Target/Safety Assignment

Assign tiers after scoring; do not let tier override poor scope fit.

| Group | Rule |
|---|---|
| Challenge | Higher tier, flagship, or more selective journal with credible scope fit |
| Target | Baseline tier with strongest overall fit |
| Safety | Lower tier or broader-scope journal with lower practical risk |

If there are not enough valid journals in a group, explain the gap instead of filling the group with weak matches.

