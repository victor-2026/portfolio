---
title: "Project: Independent Consulting — AI Quality Engineering"
---

# Project: Independent Consulting — AI Quality Engineering

**Type:** Independent practice — research, pilots, published content
**Duration:** Jan 2026 — Present (8+ months)
**Status:** Active

**Executive summary:** Independent consulting practice focused on verification quality for AI-generated code and tests. Designed and executed pilot evaluations across 23 AI testing and coding-agent tools, developed per-risk-tier attestation framework, published 20+ articles (82K peak impressions), and built a methodology that closes the gap between AI productivity claims and actual quality outcomes.

---

## Problem

The AI testing tool market is booming — but there's a verification gap. AI agents write tests fast, but:
- Who verifies the verifier?
- How do you know if a test actually catches real bugs?
- What's the difference between a test that passes and a test that proves quality?

**Core thesis:** Mutation testing as independent verification layer. If your tests can't kill mutants, they can't catch real bugs.

---

## Approach

### Framework: Per-Risk-Tier Attestation

Four risk tiers with different sensitivity thresholds:

| Tier | Risk | Threshold | Example |
|------|------|-----------|---------|
| B0 | Critical | 0/90 (no survivors) | Auth, payments |
| B1 | High | 0/80 | Core business logic |
| B2 | Medium | 1/60 | Standard features |
| B3 | Low | Vendor defaults | Cosmetic, admin |

### Featured Pilots

| Pilot | Tool | Scope | Key Finding |
|-------|------|-------|-------------|
| QAEverest | QAEverest | Per-risk-tier attestation | 100% B1 gate (414aadd), 10/10 findings |
| testRigor | testRigor | 6 mutations (M0-M4) | Plain-English: 3/6 PASS. AI-agent: 5/6 PASS |
| OrangePro | OrangePro | 122 behaviors, ranked graph | Gap analysis + reorder signal |
| Agentiqa | Agentiqa | Planetary-scale assessment | Gap analysis + pilot proposal |
| DevAssure O2 | DevAssure | Fault injection agent | Agent found bug + invented false positive |

### Published Research

- 20+ LinkedIn articles on AI testing and verification
- Peak: 82,520 impressions (3 tools, 1 app)
- Viral: 23,449 impressions (7 AI agents)
- 6,000+ followers
- Core themes: verification gap, agent reliability, boundary quality ownership

---

## Key Results

| Metric | Number | What It Means |
|--------|--------|---------------|
| Articles Published | 20+ | On AI testing, verification, quality engineering |
| Peak Impressions | 82,520 | Single post (3 AI test tools, 1 app) |
| Viral Posts | 2 | 23K and 20K+ impressions |
| Followers | 6,000+ | LinkedIn audience |
| Tools Evaluated | 23 | Executed with verdicts — full track record on the Practice page |
| Framework | v0.3 | Per-risk-tier attestation (B0-B3) |

---

## Verification Framework

**Mutation-as-evidence:** Every quality claim backed by killed mutants.

```
1. Baseline: Run test suite → all pass
2. Mutate: Introduce targeted defects (one at a time)
3. Re-run: Does the test suite catch each mutation?
4. Score: Mutations caught / total mutations = mutation score
5. Gate: Score >= tier threshold → PASS. Below → FAIL.
```

**Key insight:** A test suite that passes but can't kill mutants is theater, not quality.

---

## Links

- [AI Testing Agents 2026: 3-Month Field Report](https://www.linkedin.com/pulse/ai-testing-agents-2026-3-month-field-report-victor-ematin-s2abe/)
- [7 Desktop AI Agents: $0 Tool Beat $200/mo Tier](https://www.linkedin.com/pulse/i-spent-15-test-7-ai-agents-0-tool-beat-200mo-tier-victor-ematin-bxcvf/)
- [Conway's Law Is a Quality Engineering Problem](https://www.linkedin.com/pulse/conways-law-quality-engineering-problem-too-victor-ematin-0g5xe)
- [Who Owns Quality at the Boundaries](https://www.linkedin.com/pulse/who-owns-quality-boundaries-victor-ematin-obdce)
- [Agent Found 5 Bugs. 4 Were Imaginary.](https://www.linkedin.com/pulse/your-agent-found-5-bugs-4-were-imaginary-victor-ematin-zqcte/)
