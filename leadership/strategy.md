# Test Strategy — My Framework

## Philosophy

Test strategy is not a document. It's a pipeline. Every layer has one verifiable number, and that number ships with CI.

---

## Testing Layers

| Layer | What It Answers | Buzzhive | OrangeHRM |
|-------|----------------|----------|-----------|
| **Smoke** | "Is the system alive?" | 12 API + 28 contracts | 73 @smoke tests |
| **E2E** | "Do core flows work?" | 292 stable tests | 82 @local tests |
| **API Contract** | "Does the API match its spec?" | OpenAPI schema + Pact consumer/provider | Swagger mapped |
| **DB Integrity** | "Did the data land correctly?" | Jest + pg (follows, tokens) | Schema validation |
| **PBT** | "Do invariants hold under random inputs?" | fast-check, 7/7 methods | Table-driven patterns |
| **Mutation** | "Do tests catch injected bugs?" | 34/34 caught, 0% CFR | Fault injection suite |
| **Visual** | "Does the UI look right?" | Playwright snapshots, 3 flows | Baseline screenshots |
| **DORA Metrics** | "Are we shipping quality?" | 5 Grafana dashboards | Deployment tracking |

---

## Quality Gates

Every PR must pass all gates before merge. No exceptions.

| Gate | Tool | Fail Condition | Fix |
|------|------|---------------|-----|
| Type Check | `tsc --noEmit` | Type error | Fix types before next gate |
| Lint | ESLint | Convention violation | Follow repo conventions |
| Audit | `npm audit` | Known vulnerability | Patch or document exception |
| Smoke | Playwright | Any smoke test fails | Root cause analysis |
| Contract | ajv + Pact | Schema mismatch | Update spec + regenerate |
| Mutation | page.route() | Mutant escapes | Write test to catch it |

---

## Test Design Principles

1. **No test without a traced risk** — traceability matrix linking test cases to requirements to risks
2. **No coverage claim without a verifiable number** — every claim is backed by a CI check
3. **No AI tool without a benchmark** — cost, correctness, reliability measured per tool
4. **Budget never blocks quality** — $0 is sufficient for production-grade assurance

---

## CI/CD Architecture

```
GitHub Actions
  ├── PR Gate (typecheck, lint, audit)
  ├── Smoke Gate (12 API + 28 contract)
  ├── Nightly Gate (full suite)
  └── Mutation Gate (34 fault injections)
         │
         ▼
  Render Deploy (production)
         │
         ▼
  Uptime Monitor (cron every 6h)
```

Allure TestOps: 2 projects, 16 test plans, 162-pass launch, daily cron.

---

## Risk-Based Approach

| Risk Category | Detection Layer | Example |
|---------------|----------------|---------|
| **API schema drift** | Contract testing | OpenAPI spec vs actual response |
| **Data corruption** | DB integrity tests | Refresh token race condition |
| **Regression** | E2E + smoke | Core flow breaks after refactor |
| **Test invalidity** | Mutation testing | Test passes but doesn't actually test |
| **Visual regression** | Snapshot comparison | UI changes undetected by logic tests |
| **Performance degradation** | Smoke timing | Response time creep |
