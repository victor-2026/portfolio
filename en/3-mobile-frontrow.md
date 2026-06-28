# Project 3: Mobile Testing — FrontRow

**Type:** Cross-platform mobile test automation (iOS + Android)
**Status:** 🟡 In Progress

---

## Problem

FrontRow — open-source React Native mobile app with iOS/Android support. Broken test suite with seed date drift and race conditions.

## Approach

### Stack

| Framework | Location | Status |
|-----------|----------|--------|
| **Maestro** | `tests/maestro/` | 30 flows across 8 areas |
| **Appium (WebdriverIO + TS)** | `tests/appium/` | Smoke + login specs |
| **Espresso (Android)** | `tests/espresso/` | Smoke template |
| **XCUITest (iOS)** | `tests/xcuitest/` | Smoke + sign-in templates |

### Key Fix (2026-06-25) — 10/14 Maestro Failures Recovered

**Root cause #1 (10 flows):** Seed date drift. Events in `events.json` had past dates which `listEvents` filters out.
- Fix: evt_001 → Jul 12, evt_004 → Aug 5

**Root cause #2 (data race):** `_setup.yaml` completed before events list items rendered.
- Fix: Added `extendedWaitUntil` (10s) for event items

**Result:** 17/21 pass. All events/data flows green.
- Pre-existing failures (4): login, forgotPassword, recovery-deeplinks, edit-profile — auth flows, unrelated to events

### Infrastructure

- Cross-platform test IDs (`accessibilityIdentifier` on iOS, `resource-id` on Android)
- Centralized testID registry with ESLint enforcement
- QA Debug Menu with failure triggers, time travel, scenario seeding
- Deep link contract (`frontrow://debug/seed/<scenario>`)
- Native iOS/Android bridge testing (Swift/Kotlin)

## Results

| Metric | Before | After |
|--------|--------|-------|
| Maestro flows passing | 7/21 | 17/21 |
| Appium specs | 0 | Smoke + login |
| Espresso / XCUITest | 0 | Smoke templates |

## Next Steps

- Investigate 4 remaining auth flow failures
- Set up full Appium stack with real device cloud
- Add seed date freshness check to CI

## Tools

Maestro, Appium, WebdriverIO, TypeScript, Espresso, XCUITest, React Native
