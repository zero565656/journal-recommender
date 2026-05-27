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

## Preference Checkpoint

Use this after the strategy estimate and before any journal retrieval when the user has not already given preferences.

```markdown
## 检索前偏好确认

我已经根据摘要完成了学科和投稿策略初判。开始检索期刊前，请确认你的投稿偏好；如果没有特殊要求，也可以直接回复「默认推荐」。

1. 目标分区/收录：1区 / 2区 / 3区 / SCI/SSCI / ESCI可接受 / 不限
2. 审稿速度：越快越好 / 正常即可 / 不限制
3. 费用与OA：优先免费或无APC / APC预算 {budget} / 必须OA / 不限制
4. 投稿策略：冲稳保都要 / 只要稳妥期刊 / 优先快审 / 优先高影响力 / 你来平衡推荐
5. 其他限制：毕业时间、导师指定出版社、不要某些期刊或出版社等

你回复偏好后，我再开始检索并给出最终推荐。
```

## Internal Rough Screen

Use only as internal working notes or when the user explicitly asks to see the screening process. Do not include this section in the default final answer.

```markdown
| 分组 | 期刊名 | ISSN | IF | CAS/JCR | 主题初匹配 | 来源 |
|---|---|---|---:|---|---|---|
| 冲 | {journal} | {issn} | {if_or_unknown} | {tier} | {brief_fit} | {source} |
| 稳 | {journal} | {issn} | {if_or_unknown} | {tier} | {brief_fit} | {source} |
| 保 | {journal} | {issn} | {if_or_unknown} | {tier} | {brief_fit} | {source} |

数据抓取日期：{date}。未确认字段已标注为 `未确认`。
```

## Internal Refined Screen

Use only as internal working notes or when the user explicitly asks to see the screening process. Do not include this section in the default final answer.

```markdown
| 期刊名 | 匹配分 | Scope 证据 | 审稿/难度 | OA/APC | 风险 |
|---|---:|---|---|---|---|
| {journal} | {score}/5 | {scope_evidence} | {review_note} | {oa_note} | {risk_note} |
```

## Final Recommendation

Keep final recommendations concise but decision-useful. Preserve the challenge/target/safety strategy. Do not expand every available metadata field; show the necessary comparison fields first, then give a short, evidence-based recommendation for each journal.

```markdown
## 最终投稿推荐（冲{n_challenge} · 稳{n_target} · 保{n_safety}）

基准策略：{baseline_note}
数据抓取日期：{date}

| 推荐级别 | 期刊 | 出版商 | 匹配分 | IF | 中科院/JCR | 审稿周期 | 自引率 | 年发文量 | APC | 风险 |
|---|---|---|---:|---:|---|---|---:|---:|---|---|
| 冲 | {journal} | {publisher_or_unknown} | {score}/5 | {if_or_unknown} | {cas_jcr} | {review_time} | {self_cite_or_unknown} | {annual_articles_or_unknown} | {apc_or_unknown} | {risk_note} |
| 稳 | {journal} | {publisher_or_unknown} | {score}/5 | {if_or_unknown} | {cas_jcr} | {review_time} | {self_cite_or_unknown} | {annual_articles_or_unknown} | {apc_or_unknown} | {risk_note} |
| 保 | {journal} | {publisher_or_unknown} | {score}/5 | {if_or_unknown} | {cas_jcr} | {review_time} | {self_cite_or_unknown} | {annual_articles_or_unknown} | {apc_or_unknown} | {risk_note} |

### 🚀 冲刊建议

**{rank}. {journal_name}**

- 推荐定位：{why_challenge}
- 适配点：{scope_and_article_type_fit}
- 前人投稿经验：{experience_summary_or_insufficient_data}
- 中肯建议：{balanced_advice_considering_journal_traits_and_user_constraints}
- 来源：{official_scope_link}；{metadata_link}；{experience_source_if_any}

### 🎯 稳刊建议

**{rank}. {journal_name}**

- 推荐定位：{why_target}
- 适配点：{scope_and_article_type_fit}
- 前人投稿经验：{experience_summary_or_insufficient_data}
- 中肯建议：{balanced_advice_considering_journal_traits_and_user_constraints}
- 来源：{official_scope_link}；{metadata_link}；{experience_source_if_any}

### 🛡️ 保刊建议

**{rank}. {journal_name}**

- 推荐定位：{why_safety}
- 适配点：{scope_and_article_type_fit}
- 前人投稿经验：{experience_summary_or_insufficient_data}
- 中肯建议：{balanced_advice_considering_journal_traits_and_user_constraints}
- 来源：{official_scope_link}；{metadata_link}；{experience_source_if_any}

## 未列入推荐的风险期刊

| 期刊名 | 处理 | 原因 | 来源 |
|---|---|---|---|
| {journal} | 排除/保留警告 | {reason} | {source} |

## 投稿建议

- 若毕业时间充足，可先投冲刊；若时间紧，优先稳刊。
- 结合前人经验和期刊特性给出具体顺序：{recommended_submission_order_and_reason}
- 对 `未确认` 或风险提示字段，投稿前请与导师或学院规则确认。
- IF、分区、APC、收录状态会更新，最终以官方/索引库最新页面为准。
```

## Experience Summary Rules

When including 前人投稿经验:

- Use public, current, source-backed experience only, such as LetPub user reports or official/aggregated review statistics.
- Summarize patterns rather than quoting long passages.
- Prefer practical signals: first-decision time, common rejection reasons, editor responsiveness, reviewer strictness, revision tendency, and sample freshness.
- If evidence is thin, write `未检索到足够公开投稿经验，不做推断`.
- Do not let anecdotal experience override verified scope mismatch or hard-risk signals.

Good advice is balanced and specific:

- Good: "该刊 Scope 匹配度高且前人反馈一审多在 2-4 个月，但自引率偏高，适合作为稳刊；若学校对自引率敏感，投稿前先和导师确认。"
- Bad: "这个期刊很好，建议投。"
