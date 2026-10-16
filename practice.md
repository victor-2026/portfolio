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
| Playwright Agents (AWS) vs KISS/Sorcar | Same OrangeHRM page, head-to-head: 8 tests / 10 min (2 autofixes, 0 manual) vs 8 tests + 187-line POM in 2 prompts; both caught 6/6 seeded faults |
| Autonoma | Breadth-first: 136 NL specs across 14 modules; AI-agent eval 22/100 (4 FP) → vendor bug fixed → re-check 100/100, 0 FP |
| Kiro (AWS) | Coverage-gap audit across 2 repos: 164 tests generated (144 passed first run), 49 uncovered flows/endpoints found |
| OrangePro | Deterministic behavior mapping on OrangeHRM: 122 behaviors, 108 with no integration signal, 0 proven; same code = same score across versions 0.2.34→0.2.44 |
| Wopee | Local $0 matrix M1–M11: M8+M9 caught, zero false-pass on 10 mutations; self-heal probes audited; visual probes A PASS 97%, B/C FAIL-caught |
| Shiplight | Arm A closed (sign-off): baseline 4/4, guards caught, zero false-pass, immune to visual/text/order drift; Arm B (self-heal) not measured |
| TesterArmy | Surface A: 4/4 observable seeded spec-drift mutations caught with receipts; decoy run exposed 38 findings on a clean corpus (measured FP rate) |
| BrowserUse | Tier-1 smoke PASS end-to-end; tier-2 quality read at $0 local model: FAIL 21.4% (3/14 correct), latency PASS |
| Antigravity (Google) | 48-hour trial, clean sheet: 10 Go tests + 1 race bug + 1 Docker/nginx fix no human had flagged; trial expired, artifacts lost |
| Webwright (Microsoft Research) | ~1K-line browser agent: 50+ runs across 5 models → 1 working test; SOTA 86.67% on WebArena but ~$2.37/asset, not production-ready |
| Devin (Cognition) | Autonomous SWE agent on OrangeHRM POM: 7 tests + 4 methods generated, but text-only (blind on selectors) — 0 green runs |
| Cline | VS Code OSS agent: fit for small-file refactoring, capped by file-size limit — not adopted for test generation |
| Continue.dev | Lightweight VS Code assist — weak for QA output, dropped |
| Aider | Open source pair-programmer: 2/2 generated tests PASS, deeper than Devin thanks to its `--test-cmd` auto-fix loop (reads the failure, repairs the locator) |
| OpenCode Go | 40+ sessions on a Go API, $10 flat: 49 tests across 8 files with an infrastructure layer; found 2 race bugs |

Method in full: [How to Evaluate Any AI-QA Vendor in 5 Scenarios](https://www.linkedin.com/pulse/how-evaluate-any-ai-qa-vendor-5-scenarios-victor-ematin-lqdhe/) · [The Calculator](https://www.linkedin.com/pulse/your-vendors-green-report-claim-heres-calculator-checks-victor-ematin-gml4f/) · [RMT × VerdictGate: Can You Trust a Green Test?](https://www.linkedin.com/pulse/reverse-mutation-testing-verdictgate-can-you-trust-green-lanni-ll41e/) (joint article with Leonardo Lanni, QA Roots) · [The Guided Engineer](https://www.linkedin.com/pulse/qa-didnt-get-replaced-got-promoted-victor-ematin-9jzse/)

---

## Contact

LinkedIn DM — [Victor Ematin](https://www.linkedin.com/in/victor-ematin/). One conversation decides fit; scoped pilots only. To start I need: a system I can break, access to run seeded cases, and one engineer call.
