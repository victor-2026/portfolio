# DORA Metrics — QA Dashboard System

## Overview

DORA (DevOps Research and Assessment) metrics adapted for QA. Five Grafana dashboards tracking delivery quality in real time.

---

## Metrics Map

| DORA Metric | QA Equivalent | Measurement | Target |
|-------------|---------------|-------------|--------|
| **Deployment Frequency** | Test run frequency | Deploys/week with passing tests | Daily |
| **Lead Time for Changes** | Time from bug found to fix verified | `fix_commit_time - bug_report_time` | < 4h |
| **Change Failure Rate (CFR)** | Mutation escape rate | `escaped_mutants / total_mutants` | < 10% |
| **Mean Time to Recovery (MTTR)** | Time from failure to fix deployed | `fix_deploy_time - failure_detect_time` | < 1h |
| **Reliability** | CI/CD pass rate | `passing_runs / total_runs` | > 95% |

---

## Dashboards

| # | Dashboard | Metrics | Status |
|---|-----------|---------|--------|
| 1 | **Coverage** | API %, mutations caught, contract coverage | Live |
| 2 | **Health** | Pass/fail ratio, flaky count, run duration trend | Live |
| 3 | **Quality Gates** | Gate pass rate per type, blocking vs non-blocking | Live |
| 4 | **DORA Core** | CFR, MTTR, Lead Time, Deployment Frequency | Live |
| 5 | **AI Agent Effectiveness** | Per-tool pass rate, cost per passing test, repair rate | Live |

---

## QS Scoring (Quality Score)

Weighted metric system for comparing QA maturity across projects:

| Score | Criteria |
|-------|----------|
| 0 | No measurement |
| 0.5 | Measured, below target |
| 1 | Measured, meets target |

---

## Key Numbers

| Metric | Buzzhive | OrangeHRM |
|--------|----------|-----------|
| Tests | 330 | 200+ |
| API Coverage | 94% (49/52) | Mapped |
| CFR | 0% (34/34 caught) | In progress |
| Pass Rate | 94% | 100% (smoke) |
| CI Workflows | 5 | 4 |
| Budget | $0 | $0 |
