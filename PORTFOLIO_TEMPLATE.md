# QA/Test Lead Portfolio — Template

**For:** GitHub Pages site aggregating existing projects
**Audience:** Hiring managers, CTOs, Heads of QA
**Principle:** Every section answers "what do you lead?" — not "what did you test?"

---

## Structure

```
victor-2026.github.io/portfolio/
├── index.md                 # Landing — elevator pitch + 3 metrics at a glance
├── leadership/              # Leadership artefacts
│   ├── strategy.md          # Your QA philosophy, approach, frameworks
│   ├── metrics.md           # DORA, CFR, MTTR, coverage dashboards
│   └── ai-tools-eval.md     # AI tool evaluation framework (7 tools benchmarked)
├── projects/                # Case studies
│   ├── buzzhive.md          # Full transformation
│   ├── orangehrm.md         # Rapid bootstrap
│   └── dora-systems.md      # DORA+ metrics system
├── blog.md                  # LinkedIn articles feed (auto-generated)
└── resume.md                # CV summary (link to full PDF)
```

---

## Page 1: Landing (`index.md`)

```yaml
# Victor Ematin — AI Quality Engineering Lead

**$0 budget. Production-grade systems. Verifiable results.**

---

## At a Glance

| Metric | Number | What It Means |
|--------|--------|---------------|
| Tests | 600+ | Across 2 production-like systems, 5 testing layers |
| CI/CD Pass Rate | 94% | From 78% — zero false positives |
| API Coverage | 94% | 49/52 endpoints, contract + schema validated |
| Mutation Resilience | 34/34 caught | 0% CFR — no mutant escapes |
| AI Tools Evaluated | 7 | With benchmarked cost and ROI |
| Budget | $0 | Entire pipeline — tools, infra, reporting |

## What I Lead

Three things every project I touch gets:

1. **Test Strategy** — risk-based, layered, with verifiable coverage numbers
2. **CI/CD Quality Gates** — mutation, contract, smoke, visual — gate per type
3. **Metrics That Ship** — DORA, CFR, MTTR — dashboards, not documents

## Quick Links

- [Test Strategy →](leadership/strategy.md)
- [DORA Metrics System →](projects/dora-systems.md)
- [Buzzhive Case Study →](projects/buzzhive.md)
- [AI Tool Benchmarks →](leadership/ai-tools-eval.md)
- [LinkedIn Articles →](blog.md)
```

---

## Page 2: Strategy (`leadership/strategy.md`)

```yaml
# Test Strategy — My Framework

## Layers (Every Project)

| Layer | Purpose | Buzzhive Example | OrangeHRM Example |
|-------|---------|------------------|-------------------|
| Smoke | Health check in CI | 12 API + 28 contracts | 73 @smoke tests |
| E2E | Core flows | 292 stable tests | 82 @local tests |
| API Contract | Schema guarantees | 28 contract tests | Swagger mapped |
| Mutation | Test resilience | 34/34 caught | Fault injection suite |
| DORA Metrics | Delivery quality | 5 Grafana dashboards | Deployment tracking |

## Quality Gates

Every PR must pass before merge:

| Gate | Fail Condition | Fix |
|------|---------------|-----|
| Type check | `tsc --noEmit` fails | Fix types |
| Lint | ESLint errors | Follow conventions |
| Audit | Known vulnerabilities | Patch or document |
| Smoke | Any smoke test fails | Investigate root cause |
| Contract | Schema mismatch | Update spec + tests |

## Principles

1. No test without a traced risk (traceability matrix)
2. No coverage claim without a verifiable number
3. No AI tool without a benchmarked cost
4. Budget never blocks quality — $0 is sufficient
```

---

## Page 3: AI Tools (`leadership/ai-tools-eval.md`)

Keep the existing table from Portfolio/index.md but frame as leadership decision:

- Not "I tried these tools"
- But "I benchmarked 7 AI tools and chose the right one per use case"
- Add a "decision framework" section: cost vs capability vs maintenance overhead

---

## Page 4: DORA Metrics (`projects/dora-systems.md`)

Repurpose the existing DORA dashboard into a case study:

- What DORA metrics mean for QA
- CFR = mutation test escape rate
- MTTR = time from bug found to fix deployed
- 5 Grafana dashboards built

---

## What You Already Have (Zero New Content Needed)

| Portfolio Asset | Source Repo | Status |
|----------------|-------------|--------|
| Project case studies | `Positions-CV-CL/Portfolio/en/` | 3 ready |
| AI tool benchmarks | `Positions-CV-CL/Portfolio/index.md` | Ready |
| DORA dashboards | `Test-Dora-Plus` | Ready |
| LinkedIn articles | `Articles/linkedin-posts/` | 9 in series |
| CV in multiple formats | `Positions-CV-CL/outputs/` | Ready |

## What To Add (1 hour)

1. Strategy page — 20 minutes (your QA philosophy + layers)
2. Index page — 15 minutes (3 metrics + links)
3. GitHub Pages deploy — 5 minutes (create repo, push)

## Repo Structure

Suggested repo: `victor-2026/portfolio` → `victor-2026.github.io/portfolio`

```
portfolio/
├── index.md                 # Landing page
├── leadership/
│   ├── strategy.md
│   ├── metrics.md
│   └── ai-tools-eval.md
├── projects/
│   ├── buzzhive.md
│   ├── orangehrm.md
│   └── dora-systems.md
├── _config.yml              # Jekyll theme
├── robots.txt               # noindex
└── README.md                # Repo description
```
