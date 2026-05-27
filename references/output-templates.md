# Output Templates

These are formatting templates only. Do not reuse example journal names, metrics, APCs, or review times as facts.

## Strategy Estimate

```markdown
## 投稿策略初判

基于摘要文本信号，我建议先按「{strategy_label}/{baseline_tier}」制定投稿策略。这个判断只用于选刊分层，不代表论文真实质量；如果你的实验细节、导师目标或毕业要求不同，我会按你的约束调整。

| 维度 | 估计 | 依据 |
|---|---:|---|
| 创新性 | {score}/5 | {evidence_from_abstract} |
| 问题重要性 | {score}/5 | {evidence_from_abstract} |
| 论证充分性 | {score}/5 | {evidence_from_abstract} |
| 表达质量 | {score}/5 | {evidence_from_abstract} |

策略：冲 {challenge_tier}，稳 {target_tier}，保 {safety_tier}。
```

## Rough Screen

```markdown
## 粗筛候选期刊

| 分组 | 期刊名 | ISSN | IF | CAS/JCR | 主题初匹配 | 来源 |
|---|---|---|---:|---|---|---|
| 冲 | {journal} | {issn} | {if_or_unknown} | {tier} | {brief_fit} | {source} |
| 稳 | {journal} | {issn} | {if_or_unknown} | {tier} | {brief_fit} | {source} |
| 保 | {journal} | {issn} | {if_or_unknown} | {tier} | {brief_fit} | {source} |

数据抓取日期：{date}。未确认字段已标注为 `未确认`。
```

## Refined Screen

```markdown
## 精筛结果

### {group_label}

| 期刊名 | 匹配分 | Scope 证据 | 审稿/难度 | OA/APC | 风险 |
|---|---:|---|---|---|---|
| {journal} | {score}/5 | {scope_evidence} | {review_note} | {oa_note} | {risk_note} |
```

## Final Recommendation

```markdown
## 最终投稿推荐（冲{n_challenge} · 稳{n_target} · 保{n_safety}）

基准策略：{baseline_note}
数据抓取日期：{date}

### 🚀 冲：{tier_or_label}

**1. {journal_name}**

- ISSN：{issn_or_unknown}
- IF / 分区：{if_and_tier_with_version}
- 匹配得分：{score}/5
- 推荐理由：{scope_and_strategy_reason}
- 投稿实践：{review_speed_difficulty_oa_apc}
- 风险提示：{risk_note}
- 来源：{official_scope_link}；{metadata_link}

### 🎯 稳：{tier_or_label}

**{rank}. {journal_name}**

- ISSN：{issn_or_unknown}
- IF / 分区：{if_and_tier_with_version}
- 匹配得分：{score}/5
- 推荐理由：{scope_and_strategy_reason}
- 投稿实践：{review_speed_difficulty_oa_apc}
- 风险提示：{risk_note}
- 来源：{official_scope_link}；{metadata_link}

### 🛡️ 保：{tier_or_label}

**{rank}. {journal_name}**

- ISSN：{issn_or_unknown}
- IF / 分区：{if_and_tier_with_version}
- 匹配得分：{score}/5
- 推荐理由：{scope_and_strategy_reason}
- 投稿实践：{review_speed_difficulty_oa_apc}
- 风险提示：{risk_note}
- 来源：{official_scope_link}；{metadata_link}

## 未列入推荐的风险期刊

| 期刊名 | 处理 | 原因 | 来源 |
|---|---|---|---|
| {journal} | 排除/保留警告 | {reason} | {source} |

## 投稿建议

- 若毕业时间充足，可先投冲刊；若时间紧，优先稳刊。
- 对 `未确认` 或风险提示字段，投稿前请与导师或学院规则确认。
- IF、分区、APC、收录状态会更新，最终以官方/索引库最新页面为准。
```

