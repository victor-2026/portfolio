---
title: "Independent Practice — AI-QA Verification"
---

# Independent Practice — Verifying AI Testing Tools

**Victor Ematin · AI Quality Engineering Lead · Independent practice (no company, no sales)**

I independently verify AI-powered QA tools: seed known breaks, check whether the tool catches them, deliver a verdict with evidence. Methodology and tooling are open; findings go to the vendor privately first; nothing publishes without consent.

---

## How it works

1. **Seeded breaks** — known defects planted in a test system (mutated UI, drifted locators, broken submits).
2. **Verdict with evidence** — per-risk-tier gate (critical paths: zero tolerance; lower tiers: bounded bands), every verdict backed by an evidence pack.
3. **Findings first, privately** — the vendor gets everything before anyone else.
4. **Publish only with consent** — naming and numbers are agreed, never assumed.

Open methodology + open tooling: [VerdictGate](https://github.com/victor-2026/verdictgate) (mutation-matrix verdict calculator, MIT).

---

## Track record

| Pilot | Result |
|-------|--------|
| QAEverest (DevQAExpert) | Seeded breaks missed 0/4 → gated red; relevance + tolerance semantics co-drafted |
| Agentiqa | 0/6 survived across UI mutants; cold-start memory effect documented |
| qa-cube | 120 validation runs, 35 min, zero product defects — clean attestation |
| OpenClaw | RMT batches 53/58 + 22/24 killed; survivors adjudicated 1+2+2 |
| testRigor, FlowScout, DevAssure | Text-vs-locator healing, auth-walled crawl fixes, FP regression audit |

Method in full: [How to Evaluate Any AI-QA Vendor in 5 Scenarios](https://www.linkedin.com/pulse/how-evaluate-any-ai-qa-vendor-5-scenarios-victor-ematin-lqdhe/) · [The Calculator](https://www.linkedin.com/pulse/your-vendors-green-report-claim-heres-calculator-checks-victor-ematin-gml4f/) · [The Guided Engineer](https://www.linkedin.com/pulse/qa-didnt-get-replaced-got-promoted-victor-ematin-9jzse/)

---

## Contact

LinkedIn DM — [Victor Ematin](https://www.linkedin.com/in/victor-ematin/). One conversation decides fit; scoped pilots only, no retainers up front.
