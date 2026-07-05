---
title: "Project: LinkedIn Performance Analyzer"
---

# LinkedIn Performance Analyzer — DS/ML for Content Analytics

**Type:** Applied DS/ML QA — Go CLI tool
**Data:** 48 records, 42 posts (Apr–Jul 2026)
**Status:** ✅ Active, updated weekly

---

## Problem

LinkedIn provides aggregate analytics but no structured way to benchmark post performance, detect engagement drift, or compare format effectiveness over time. Manual analysis of 40+ posts takes hours.

## Approach

Applied the same 4-level DS/ML testing methodology used for financial algorithms to content analytics:

```
Live Data (CSV)
  └── PBT Layer — invariant checks (impressions > 0, dates not in future)
        └── A/B Gate — hashtag & format comparison (article vs carousel vs post)
              └── Drift Detection — weekly engagement degradation signals
                    └── Golden Dataset — P50/P90 benchmarks for new posts
```

### Architecture

| Layer | DS/ML Concept | Implementation |
|-------|---------------|----------------|
| **1. PBT** | Model invariants | Row-level validation: impressions, dates, format strings |
| **2. A/B Gate** | Model comparison | Hashtag ranking by avg impressions, format effectiveness |
| **3. Drift** | Concept drift | Sliding window: 4-week vs 1-week engagement comparison |
| **4. Golden Dataset** | Regression test set | P50 (median) and P90 benchmarks for future posts |

### Tech Stack

Go 1.26, `encoding/csv`, `flag` (stdlib only — zero dependencies).

## Results

| Metric | Value | What It Means |
|--------|-------|---------------|
| Records validated | 48 (42 with metrics) | Automated PBT catch: 6 rows skipped (no numeric data) |
| Avg impressions | 669 | Expected reach per post |
| P50 (median) | 336 | Half of posts exceed this |
| P90 | 1,533 | Top 10% performance threshold |
| Best format | article (1,003 avg imp) | 2.6x better than posts (380 avg) |
| Drift window | W20–W27 | Engagement degradation flagged, 2 format changes triggered |
| Top hashtag | #TestAutomation | Consistent top performer across formats |

### 90-Day Confirmed Metrics (LinkedIn Aggregate, Apr 7 – Jul 5)

| Metric | Value |
|--------|-------|
| Total impressions | 23,682 |
| Members reached | 11,998 |
| Followers | 1,125 |
| Top post | Article 7 — 2,552 imp |
| Best engagement | QA Engineer AI Testing — 17 engagements |
| Senior audience | 38% Senior, 12% Director, 7% CXO |

## Key Insights

1. **Articles outperform posts 2.6x** — the format decision alone doubles reach
2. **Drift detection works** — W23 engagement drop triggered format shift from posts to articles
3. **P90 benchmark** of 1,533 sets realistic target — not vanity metrics
4. **Zero dependencies** — the entire tool is one Go file with stdlib only

## Tools

Go 1.26, LinkedIn Aggregate Analytics, GitHub (version control), Obsidian (frontmatter templates)

## How It Runs

```bash
go run ./code/linkedin-analyzer/ performance-log.csv
```

Output: hashtag ranking, format comparison, drift table, golden dataset benchmarks.
