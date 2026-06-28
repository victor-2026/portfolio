---
title: "Project: OrangeHRM"
---

# Project 2: OrangeHRM — Rapid Bootstrap → Full Coverage

**Type:** Broad — enter unfamiliar system, deliver working tests in one session
**Duration:** Multiple sessions (~20 hours total)
**Status:** ✅ Complete

---

## Problem

Open-source HRM system (12 modules: Admin, PIM, Leave, Time, Recruitment, etc.) with no test suite. OrangeHRM upgraded from 5.4 to 5.8.1 during the project.

## Approach

### Strategy

1. **Exploration-first** — Playwright MCP script mapped 12 modules + took 14 screenshots in 15 seconds
2. **POM scaffold** — Page Object Model aligned to OrangeHRM module hierarchy
3. **Seed test** — `e2e/seed.spec.ts` logs in as admin, saves `storageState` → all modules reuse auth
4. **Playwright Agents** — Planner explores, Generator creates, Healer repairs

### Module Coverage (16 modules, 82 @local tests)

| Module | @local tests | Module | @local tests |
|--------|:------------:|--------|:------------:|
| Admin | 18 | Claim | 14 |
| MyInfo | 7 | Dashboard | 4 |
| Recruitment | 6 | Buzz | 6 |
| Time | 4 | Auth | 4 |
| Leave | 4 | PIM | 3 |
| Performance | 3 | Maintenance | 3 |
| Directory | 3 | Fault-injection | 2 |

### AI Tools Applied

| Tool | Result |
|------|--------|
| **KISS Sorcar** | $0.19, 1st try POM + test, auto-repair on 2 selector failures |
| **Playwright Agents** | Planner fixtures (adminSession, setupAdminTestData), Healer fixed stale selectors |
| **Cline** | Tested, fell over large files |
| **Continue.dev** | Tested, minimal value |

### Docker Local Environment

- OrangeHRM 5.8.1 on Docker Desktop 29.5.2
- ~1.5 GB RAM, MacBook
- DB migration: 1,083,396 bytes, 175 tables preserved
- Credentials: `Admin` / `Orangehrm@2026`

## Results

| Metric | Value |
|--------|-------|
| Modules mapped | 16/16 |
| @local tests | 82 |
| @smoke tests | 66 |
| Smoke suite | 73/73 pass in 2.2m |
| Auth project | 4/4 pass in 9.8s |
| POMs | 13 |
| Test projects in config | 5 (setup, smoke, chromium, auth, local, visual) |

## Tools

Playwright, TypeScript, POM, Playwright MCP, KISS Sorcar, Playwright Agents,
Docker, OrangeHRM 5.8.1, Allure TestOps
