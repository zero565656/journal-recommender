# Data Sources

Use current sources for journal facts. Do not rely on memory for publisher, impact factor, CAS/JCR tier, APC, indexing, review time, self-citation rate, annual article volume, warning-list status, author experiences, or URLs.

## Preferred Source Order

| Data | Prefer | Fallback |
|---|---|---|
| Aims & Scope | Official journal or publisher page | LetPub topic fields or journal description |
| Publisher | Official journal page, publisher page, or current indexing record | LetPub/current aggregator, marked as unverified |
| CAS partition | LetPub page-displayed "新锐期刊分区表" or current CAS source | Other current aggregators, with disclosure |
| JCR quartile / IF | Journal Citation Reports or page-displayed source | LetPub/current aggregator, with date |
| Indexing | Web of Science, Scopus, PubMed, DOAJ, official journal page | Aggregator metadata, marked as unverified |
| APC/OA | Official publisher APC/OA page | LetPub/DOAJ, marked as approximate |
| Review speed/difficulty | LetPub journal page and recent user reports | Publisher process estimates, marked as general |
| Self-citation rate | JCR, LetPub, or current journal metrics page | Aggregator metadata, marked as unverified |
| Annual article volume | JCR, Scopus, Web of Science, LetPub, or publisher archive | Count/estimate from recent issue archive, marked as approximate |
| Author submission experience | LetPub recent user reports or other public, dated reports | Mark as insufficient evidence instead of guessing |
| Risk status | CAS warning list, Beall-style lists, DOAJ/COPE/indexing checks | Manual warning with incomplete verification |

## LetPub Query References

Read `cas-subjects.md` for `fieldtag` values and search URL examples.

Common patterns:

```text
https://www.letpub.com.cn/index.php?page=journalapp&view=researchfield&fieldtag={fieldtag}&firstletter=
https://www.letpub.com.cn/index.php?page=journalapp&view=search&searchfield={field}&searchcasnewranking={1|2|3|4}&searchimpactlow={min_if}&page_number=1
https://www.letpub.com.cn/index.php?page=journalapp&view=detail&journalid={journalid}
```

Use available browsing/search/page-fetch tools in the current environment. Do not assume a tool has a specific name.

## Version And Date Rules

- Report the retrieval date for time-sensitive data.
- Use the source page's displayed version when available.
- Do not hard-code "2026年3月版" or any fixed version unless the source page explicitly shows it.
- If sources disagree, prefer official publisher/indexing data, then explain the discrepancy.

## Fallback Rules

- If a primary metadata source fails, try an equivalent source and disclose the substitution.
- If no current source is accessible, stop before making journal recommendations.
- If only partial data is available, recommend only when scope fit and risk status are sufficiently supported; mark missing fields as `未确认`.
- If author experience data is sparse, stale, or unavailable, write `未检索到足够公开投稿经验，不做推断`; do not invent review experiences.
- For final comparison tables, prioritize the necessary decision fields: recommendation level, journal, publisher, fit score, IF, CAS/JCR, review time, self-citation rate, annual article volume, APC, and risk.
