---
title: AI Tool Evaluation
---

# AI Tool Evaluation — 9 Tools Benchmarked

## Decision Framework

Every AI tool evaluated across 4 axes before adoption:

| Axis | What It Measures | Fail Condition |
|------|-----------------|----------------|
| **Cost** | $ per passing test | > $3/test = not viable for CI |
| **Correctness** | % of generated tests that compile and pass | < 50% = not usable |
| **Reliability** | Same input → same output across 3 runs | Variance > 20% = unreliable |
| **Maintenance** | Time to fix AI-generated output vs writing manually | Longer = net negative |

---

## Tool Comparison

| Tool | Type | Cost | Pass Rate | Best For | Verdict |
|------|------|------|-----------|----------|---------|
| **KISS Sorcar** | CLI coding agent | $0.19 total | 3/3 tests | Executable test generation with auto-repair | ✅ Adopted |
| **Cline** | VS Code agent (OSS) | API only | N/A (file size cap) | Small-file refactoring | ⚠️ Limited |
| **Continue.dev** | VS Code extension | API only | Weak | Lightweight code assist | ❌ Dropped |
| **Antigravity** | Google agent platform | Free preview | 10 Go tests, 1 race bug | Go test generation, race detection | ⚠️ Access lost |
| **Devin** | Autonomous web agent | ~~$500/mo~~ Free (2026) | Pending | Full test suite generation, auto-debug | ⚠️ Free now — pending re-evaluation |
| **Webwright (MS)** | Research-grade agent | $2.37/test | Research-grade | Exploration, benchmarking | ⚠️ Not production |
| **Autonoma** | SaaS agent pipeline | $3.62 total | 4/6 steps (overflow at entityAudit) | Full codebase exploration + test gen | ⚠️ Useful but expensive; model auto-switching risk |
| **Playwright Agents** | 3-agent pipeline | Free | Healer: 3/6 bugs fixed | Visual test repair, infrastructure fixes | ✅ For visual |

---

### Deep Eval: Autonoma Context Overflow

Autonoma's 6-step pipeline works well for steps 1-2 (<131K context) but hits overflow at step 3 (entityAudit: 274K) and times out at step 4 (scenarioRecipe: 191K). Guidance (skip POMs) reduces entityAudit to 59 entities but doesn't fully resolve the issue. The model auto-switched from deepseek → kimi → deepseek-pro → gpt-5.4-nano without asking — a budget control risk.

---

## Key Decision: KISS Sorcar vs Autonoma

| Dimension | KISS Sorcar | Autonoma |
|-----------|-------------|----------|
| Model | gpt-4o | gpt-4o + deepseek |
| Pipeline | 1-step generation | 6-step (explore → generate → validate) |
| Total cost | $0.19 | $3.62 |
| Cost per module | $0.046 | $0.72 |
| Auto-repair | Yes (auto retry on failure) | No (must relaunch) |
| Best for | Executable test generation | Full exploration + generation |

**Decision:** KISS for quick generation. Autonoma for deep exploration of unfamiliar codebases.  
Detailed experiment breakdown: [KISS vs Autonoma — LinkedIn](https://www.linkedin.com/pulse/one-agent-discovered-13-modules-other-wrote-working-code-ematin-651ze/).

---

### Playwright Agents in Practice

Healer fixed 3/6 bugs in visual tests. Data-level bugs required human judgment. Full analysis: [Playwright Test Agents — LinkedIn](https://www.linkedin.com/posts/victor-ematin_testautomation-aitesting-playwright-ugcPost-7472448714876325888-OBLW).

---

## AI Testing Principles Applied

1. **Never trust AI output without validation** — mutation tests verify tests, tests verify code
2. **Benchmark before adopting** — 4-axis framework above, applied to every tool
3. **Self-evaluation is insufficient** — same model grading itself = 0% lift (verified with 18 runs)
4. **BDD harness as validation layer** — Given-When-Then specs execute against AI output, drift = build failure
