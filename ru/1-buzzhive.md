# Проект 1: Buzzhive — Полная трансформация

**Тип:** Глубокая — legacy → production-grade QA-система
**Длительность:** 8 сессий (~26 часов)
**Статус:** ✅ Завершён

---

## Проблема

Multi-product SaaS платформа (posts, conversations, notifications, admin) с:
- Монолитными тестовыми наборами (2349 строк в одном файле, 1559 в другом)
- 40+ `waitForTimeout`, вызывающих flaky-падения
- Отсутствием документации API-покрытия (55+ Swagger endpoint'ов без тестов)
- Отсутствием CI/CD quality gates
- Бюджетом $0

## Подход

### Слои тестирования

| Слой | Инструмент | Что проверяет |
|------|-----------|---------------|
| E2E | Playwright | UI-поведение в 4 браузерах |
| API | Playwright + fetch | 49/52 endpoint'ов — схема, статус, авторизация |
| DB | Jest + pg | Целостность данных |
| PBT | fast-check | 13 core API, 100+ случайных входов |
| BDD | Cucumber + Gherkin | Критерии приёмки |
| Contract | ajv + Pact | Схема (17) + consumer-driven (9) + provider (2) |
| Mutation | page.route() | 34 fault injection — API, DB, chaos, UI fuzz |
| Visual | Playwright snapshots | Визуальная регрессия |

### Go / Antigravity (Новый слой)

33 Go теста:
- 24 API теста (net/http + testify): Auth (8), Posts (5), Users (6), Follows (5)
- 9 Playwright Go (браузер): логин, регистрация, SQL injection

### Оценка AI-инструментов

| Инструмент | Стоимость | Результат |
|-----------|-----------|-----------|
| **KISS Sorcar** | $0.19 | 3/3 тестов с авто-ремонтом |
| **Cline** | API costs | Не справился с файлами >2000 строк |
| **Continue.dev** | API costs | Минимальный вклад |
| **Antigravity** | Бесплатно | 10 Go тестов, найден race bug |
| **Devin** | $500/мес | Только исследование |
| **Webwright (MS)** | $2.37/тест | Research-grade, 2 патча |
| **Playwright Agents** | Бесплатно | Healer починил 3 visual failures |

### CI/CD Pipeline

4 GitHub Actions workflow: uptime, nightly, contracts (28/28), mutation (34/34)
Allure TestOps: 2 проекта, 16 test plans, ежедневный cron
Grafana: 5 DORA дашбордов

## Результаты

| Метрика | До | После |
|---------|----|-------|
| Структура | 2 монолита (4000 строк) | 23 модульных файла |
| API покрытие | 0% | 94% (49/52 endpoint'ов) |
| Flaky-тесты | Много | 0 |
| CI/CD pass rate | 78% | 94% |
| Бюджет | $0 | $0 |

## Инструменты

Playwright, TypeScript, Go, Jest, pg, fast-check, Cucumber, Pact,
Ollama, Groq, OpenCode, KISS, Cline, Continue, Antigravity,
GitHub Actions, Render, Allure TestOps, Grafana
