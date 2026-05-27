# Journal Recommender Skill

`journal-recommender` is an Agent Skill for recommending academic journals from a manuscript abstract. It is designed for graduate students and researchers who need a practical shortlist of journals for submission.

The skill combines abstract-based topic matching, current journal metadata, official Aims & Scope evidence, CAS/JCR ranking, review-speed and OA/APC considerations, and publication-risk checks.

It follows the open Agent Skills style and can be used in skills-compatible agent runtimes such as Claude Code, Codex, Cursor, OpenClaw, and similar tools.

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

`SKILL.md` contains the core workflow and points the agent to the reference files only when needed. The reference files hold the longer scoring rules, data-source guidance, risk checks, and output templates.

## Installation

### Option 1: One-line install

If your agent runtime supports skill installation, ask the agent directly:

```text
帮我安装这个 skill：https://github.com/zero565656/journal-recommender
```

Or use the general skills installer:

```bash
npx skills add zero565656/journal-recommender
```

If needed, specify the target agent/runtime:

```bash
npx skills add zero565656/journal-recommender -a codex
npx skills add zero565656/journal-recommender -a claude-code
npx skills add zero565656/journal-recommender -a cursor
npx skills add zero565656/journal-recommender -a openclaw
```

### Option 2: Manual install

Clone this repository into the skills directory used by your agent runtime.

| Runtime | Install path |
|---|---|
| Claude Code | `~/.claude/skills/journal-recommender/` |
| Codex CLI | `~/.codex/skills/journal-recommender/` |
| Cursor | `~/.cursor/skills/journal-recommender/` |
| OpenClaw | `~/.openclaw/workspace/skills/journal-recommender/` |
| Other skills-compatible agents | Clone into that runtime's `skills/` directory |

macOS / Linux:

```bash
git clone https://github.com/zero565656/journal-recommender.git ~/.codex/skills/journal-recommender
```

Windows PowerShell:

```powershell
$skills = "$env:USERPROFILE\.codex\skills"
New-Item -ItemType Directory -Force $skills | Out-Null
git clone https://github.com/zero565656/journal-recommender.git "$skills\journal-recommender"
```

Replace the destination path if you are installing for Claude Code, Cursor, OpenClaw, or another runtime.

Restart your agent after installation so the skill can be discovered.

### Option 3: Use as a reference

If your agent does not support Agent Skills auto-loading, open `SKILL.md` and paste its contents into your conversation as instructions. The skill is plain Markdown with YAML frontmatter plus reference files.

## Updating

Go to the installation path for your runtime, then pull the latest version:

```bash
cd ~/.codex/skills/journal-recommender
git pull
```

On Windows PowerShell:

```powershell
cd "$env:USERPROFILE\.codex\skills\journal-recommender"
git pull
```

Replace the path if you installed it under Claude Code, Cursor, OpenClaw, or another runtime.

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
