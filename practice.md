---
title: "Independent Practice — AI-QA Verification"
---

# Independent Practice — Verifying AI Testing Tools

**Victor Ematin · AI Quality Engineering Lead · Independent practice — paid only by results, never up front**

I independently verify AI-powered QA tools: seed known breaks, check whether the tool catches them, deliver a verdict with evidence. Methodology and tooling are open; findings go to the vendor privately first; nothing publishes without consent.

---

## How it works

1. **Seeded breaks** — known defects planted in a test system (mutated UI, drifted locators, broken submits).
2. **Verdict with evidence** — per-risk-tier gate (critical paths: zero tolerance; lower tiers: bounded bands), every verdict backed by an evidence pack.
3. **Findings first, privately** — the vendor gets everything before anyone else.
4. **Publish only with consent** — naming and numbers are agreed, never assumed.

**Scope guard:** I verify, I don't fix — no implementation, no remediation.

Open methodology + open tooling: [VerdictGate](https://github.com/victor-2026/verdictgate) (mutation-matrix verdict calculator, MIT).

---

## Track record

| Pilot | Result |
|-------|--------|
| QAEverest (DevQAExpert) | Initial batch: caught 0 of 4 seeded breaks → FAIL (red gate); relevance + tolerance semantics co-drafted |
| Agentiqa | 0/6 mutants survived — 4 adapted correctly, 2 killed correctly; cold-start memory effect documented (cold runs fail where warm pass) |
| qa-cube | 120 validation runs in ~35 min, 100% success |
| OpenClaw | RMT batches: 53/58 killed (5 survivors adjudicated 1+2+2); 22 killed outright, 0 survived, 2 error-terminated shown |
| testRigor, FlowScout, DevAssure | M0–M4 verified 3+3; v0.6.2 retest + port fix, both paths verified; re-check 100/100, pilot closed |

Method in full: [How to Evaluate Any AI-QA Vendor in 5 Scenarios](https://www.linkedin.com/pulse/how-evaluate-any-ai-qa-vendor-5-scenarios-victor-ematin-lqdhe/) · [The Calculator](https://www.linkedin.com/pulse/your-vendors-green-report-claim-heres-calculator-checks-victor-ematin-gml4f/) · [The Guided Engineer](https://www.linkedin.com/pulse/qa-didnt-get-replaced-got-promoted-victor-ematin-9jzse/)

---

## Contact

LinkedIn DM — [Victor Ematin](https://www.linkedin.com/in/victor-ematin/). One conversation decides fit; scoped pilots only. To start I need: a system I can break, access to run seeded cases, and one engineer call.
