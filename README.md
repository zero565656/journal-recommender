# Journal Recommender Skill

`journal-recommender` is a Codex skill for recommending academic journals from a manuscript abstract. It is designed for graduate students and researchers who need a practical shortlist of journals for submission.

The skill combines abstract-based topic matching, current journal metadata, official Aims & Scope evidence, CAS/JCR ranking, review-speed and OA/APC considerations, and publication-risk checks.

## What It Does

- Identifies the manuscript's main discipline and optional secondary disciplines.
- Estimates a tentative submission strategy from abstract signals.
- Builds a challenge / target / safety journal pool.
- Uses current web data instead of relying on memory for IF, rankings, APCs, indexing, or review time.
- Scores journals using evidence from LetPub or equivalent metadata pages, official journal pages, and Aims & Scope text.
- Flags publication risks such as warning-list status, ESCI-only indexing, high self-citation, unclear APCs, or incomplete verification.
- Produces a concise final recommendation, usually `challenge 2 + target 2 + safety 1`.

## When To Use

Use this skill when a user asks things like:

- "推荐几个适合这篇论文投稿的期刊"
- "我的论文适合投什么期刊？"
- "帮我选刊"
- "Which journals should I submit this paper to?"
- "Find 3-5 suitable journals for this abstract"

## Repository Structure

```text
journal-recommender/
├── SKILL.md
└── references/
    ├── cas-subjects.md
    ├── data-sources.md
    ├── output-templates.md
    ├── risk-checks.md
    └── scoring-rubric.md
```

`SKILL.md` contains the core workflow and points Codex to the reference files only when needed. The reference files hold the longer scoring rules, data-source guidance, risk checks, and output templates.

## Installation

Clone this repository into your Codex skills directory.

### Windows PowerShell

```powershell
$skills = "$env:USERPROFILE\.codex\skills"
New-Item -ItemType Directory -Force $skills | Out-Null
git clone https://github.com/zero565656/journal-recommender.git "$skills\journal-recommender"
```

### macOS / Linux

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/zero565656/journal-recommender.git ~/.codex/skills/journal-recommender
```

Restart Codex after installation so the skill can be discovered.

## Updating

```bash
cd ~/.codex/skills/journal-recommender
git pull
```

On Windows PowerShell:

```powershell
cd "$env:USERPROFILE\.codex\skills\journal-recommender"
git pull
```

## Example Prompt

```text
Use journal-recommender. Here is my abstract:

[Paste abstract here]

I prefer SCI journals, CAS 1-2区 if possible. My deadline is about 8 months, and APC should be under $3000.
```

## Notes

- The skill requires current web access for reliable journal recommendations.
- It should not fabricate journal facts from memory.
- Abstract-only tiering is a submission-strategy estimate, not an objective judgment of manuscript quality.
- Final submission decisions should still be checked against supervisor advice, school graduation requirements, and the journal's official website.

