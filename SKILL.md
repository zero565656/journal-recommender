---
name: journal-recommender
description: Use when the user asks for journal recommendation, 选刊, 投稿期刊筛选, 期刊匹配, 适合投稿的期刊, 投哪个期刊, or wants 3-5 suitable journals for a manuscript based on an abstract, discipline, CAS/JCR ranking, impact factor, Aims & Scope, review speed, OA/APC, and publication-risk checks.
---

# Journal Recommender

Recommend journals for a manuscript by combining abstract-based fit, current journal metadata, official Aims & Scope evidence, and publication-risk checks. Use Chinese for explanations unless the user requests otherwise; keep journal names in their official English form.

## Core Workflow

1. Read the abstract and identify the main discipline, optional secondary disciplines, research type, and 3-5 English keywords.
2. Make a **submission strategy estimate**, not a quality verdict: infer a tentative baseline CAS tier from abstract signals and ask the user to correct it if needed.
3. Stop before web search and ask for submission preferences unless the user already supplied them or explicitly says to use defaults.
4. Collect current journal data from available web/search/page-fetch tools. Do not rely on memory for IF, CAS/JCR tiers, APCs, review time, indexing, warning-list status, or URLs.
5. Build a challenge/target/safety pool:
   - `challenge`: one tier above the baseline, or field flagship journals when baseline is already CAS 1.
   - `target`: the baseline tier and strongest scope match.
   - `safety`: one tier below the baseline, prioritizing fit and lower practical risk.
6. Score candidates with evidence from LetPub or equivalent journal pages, official publisher pages, and Aims & Scope text.
7. Apply hard exclusions and soft warnings, then output only the final 3-5 journal recommendations, preferably `challenge 2 + target 2 + safety 1` when enough valid candidates exist.

## Load References

- Read `references/cas-subjects.md` when mapping a discipline to LetPub `fieldtag` or search parameters.
- Read `references/scoring-rubric.md` before estimating baseline tier or scoring journal fit.
- Read `references/data-sources.md` before fetching journal data or when a source is unavailable.
- Read `references/risk-checks.md` before final filtering.
- Read `references/output-templates.md` when formatting the preference checkpoint or final recommendations.

## Required User Inputs

After parsing the abstract and giving the tentative strategy estimate, ask once for the user's submission preferences before any web search. If the user has already supplied these constraints, summarize them and proceed without repeating questions.

- Target outcome: CAS/JCR tier, SCI/SSCI requirement, or "no strict target".
- Constraints: graduation deadline, review-speed needs, IF floor, OA/APC budget, rejected publishers/journals, supervisor preferences.
- Tolerance: whether to include challenge journals or only practical target/safety journals.
- Cost preference: free/no APC, low APC, OA required, or no preference.
- Practical priority: higher impact, faster review, safer graduation, lower cost, or balanced recommendation.

When the user only provides an abstract, do not begin retrieval immediately. Ask the preference checkpoint question. Use defaults only when the user explicitly says "你来推荐", "默认即可", "无偏好", or equivalent: `challenge + target + safety`, no IF floor, no TOP-only filter, APC unknown acceptable but must be disclosed.

## Submission Strategy Estimate

Treat abstract-only tiering as a rough strategy estimate. Never present it as an objective judgment of manuscript quality.

Use the rubric in `references/scoring-rubric.md` to estimate:

- novelty signal
- problem importance
- evidence strength
- writing clarity

Then state the baseline as tentative:

```markdown
基于摘要文本信号，我建议先按「中上/2区基准」制定投稿策略。这个判断只用于选刊分层，不代表论文真实质量；如果你的实验、数据或导师目标更高/更保守，我会按你的判断调整。
```

## Preference Checkpoint

Before retrieval, pause and ask the user to choose preferences. Keep the question compact and allow the user to answer "默认推荐".

Ask for:

- target tier or indexing: CAS/JCR tier, SCI/SSCI/ESCI/Scopus, or no strict target
- review speed: fast review needed, normal, or no preference
- cost/OA: free/no APC preferred, APC budget, OA required, or no preference
- strategy: challenge/target/safety, conservative only, or let the agent decide
- extra constraints: graduation deadline, rejected journals/publishers, supervisor preference

Do not start web retrieval until the user answers, unless the initial request already includes enough preferences or explicitly delegates the decision to the agent.

## Search And Screening Rules

- Prefer current web data. If network tools are unavailable, say so and stop before fabricating recommendations.
- Use available browsing/search/fetch tools; do not assume a tool named `web_fetch` exists.
- Record the source URL and retrieval date for each journal when possible.
- Use page-displayed versions for IF and CAS/JCR data; do not hard-code a month or year.
- If a data field cannot be verified, mark it `未确认` and do not award positive score from that field.
- If Aims & Scope cannot be accessed, use LetPub/reliable journal-topic fields as a fallback and cap discipline-fit score at 3/5.
- For interdisciplinary manuscripts, search the main discipline first, then up to two secondary disciplines; deduplicate by normalized journal name and ISSN.

## Evidence Requirements

Every final recommendation must include enough evidence for a user to audit the result:

- journal name, ISSN if available, IF, CAS/JCR tier, indexing status if relevant
- scope-fit reason tied to Aims & Scope or verified topic fields
- practical note: review speed, difficulty, OA/APC, or missing data
- risk status: no known issue, warning, excluded, or unable to verify
- links to official journal page/Aims & Scope and metadata source

Do not reuse concrete example journal data from templates as facts. Templates are formatting examples only.

## Interaction Policy

- Always ask the preference checkpoint after abstract parsing and before retrieval when preferences are missing.
- Ask other clarifying questions only when required constraints are missing or the user must choose among materially different strategies.
- Do not stop after each layer waiting for permission. Continue through rough screening, refined scoring, and risk filtering in one pass when data access and user preferences are sufficient.
- Do not show rough-screen or refined-screen candidate tables by default; keep them as internal working notes. Show intermediate candidate pools only when the user explicitly asks to see the screening process.
- If candidate count is too large, prioritize target and challenge journals first, then add safety journals to complete the final set.
- If the field has fewer than five viable candidates, explain the shortage and suggest widening tier, discipline, indexing, or OA constraints.

## Failure Handling

- Primary metadata source unavailable: try an equivalent source, then disclose the substitution.
- Official Aims & Scope unavailable: use fallback topic fields, cap scope-fit score at 3/5, and mark the limitation.
- Risk-list source unavailable: do not claim a journal is safe; mark blacklist/warning-list verification as incomplete.
- Conflicting source data: prefer official publisher/indexing pages over aggregator pages, and show the conflict briefly.
