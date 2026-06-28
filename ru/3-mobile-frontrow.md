# Проект 3: Mobile — FrontRow

**Тип:** Кросс-платформенная мобильная автоматизация (iOS + Android)
**Статус:** 🟡 В разработке

---

## Проблема

FrontRow — open-source React Native приложение для iOS/Android. Сломанный набор тестов: дрейф дат в seed-данных и race condition.

## Подход

### Стек

| Фреймворк | Расположение | Статус |
|-----------|-------------|--------|
| **Maestro** | `tests/maestro/` | 30 flows, 8 областей |
| **Appium (WebdriverIO + TS)** | `tests/appium/` | Smoke + login |
| **Espresso (Android)** | `tests/espresso/` | Smoke шаблон |
| **XCUITest (iOS)** | `tests/xcuitest/` | Smoke + sign-in |

### Ключевое исправление (2026-06-25) — 10/14 Maestro failures починены

**Причина #1 (10 flows):** Даты в `events.json` были в прошлом → `listEvents` фильтровал.
- Исправление: evt_001 → 12 июля, evt_004 → 5 августа

**Причина #2 (race condition):** `_setup.yaml` завершался до отрисовки списка событий.
- Исправление: `extendedWaitUntil` (10с) для event items

**Результат:** 17/21 pass. Все events/data flows зелёные.

### Инфраструктура

- Кросс-платформенные testID (`accessibilityIdentifier` на iOS, `resource-id` на Android)
- QA Debug Menu: failure triggers, time travel, scenario seeding
- Deep link контракт (`frontrow://debug/seed/<scenario>`)
- Нативные iOS/Android мосты (Swift/Kotlin)

## Результаты

| Метрика | До | После |
|---------|----|-------|
| Maestro flows проходят | 7/21 | 17/21 |
| Appium specs | 0 | Smoke + login |
| Espresso / XCUITest | 0 | Smoke шаблоны |

## Следующие шаги

- Разобрать 4 оставшихся auth-падения
- Развернуть полный Appium стек с real device cloud
- Добавить проверку свежести seed-дат в CI

## Инструменты

Maestro, Appium, WebdriverIO, TypeScript, Espresso, XCUITest, React Native
