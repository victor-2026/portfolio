# Проект 2: OrangeHRM — Быстрый старт → Полное покрытие

**Тип:** Широкий — войти в незнакомую систему, выдать работающие тесты за одну сессию
**Длительность:** Несколько сессий (~20 часов)
**Статус:** ✅ Завершён

---

## Проблема

Open-source HRM система (12 модулей) без единого теста. OrangeHRM обновлён с 5.4 до 5.8.1 во время проекта.

## Подход

1. **Exploration-first** — Playwright MCP за 15 секунд: 12 модулей, 14 скриншотов
2. **POM scaffold** — Page Object Model по иерархии модулей OrangeHRM
3. **Seed test** — `e2e/seed.spec.ts` — единая авторизация для всех модулей
4. **Playwright Agents** — Planner → Generator → Healer

### Покрытие модулей (16 модулей, 82 @local теста)

| Модуль | Тестов | Модуль | Тестов |
|--------|:------:|--------|:------:|
| Admin | 18 | Claim | 14 |
| MyInfo | 7 | Dashboard | 4 |
| Recruitment | 6 | Buzz | 6 |
| Time | 4 | Auth | 4 |
| Leave | 4 | PIM | 3 |
| Performance | 3 | Maintenance | 3 |
| Directory | 3 | Fault-injection | 2 |

### AI-инструменты

| Инструмент | Результат |
|-----------|-----------|
| **KISS Sorcar** | $0.19, POM + тест с первой попытки, авто-ремонт селекторов |
| **Playwright Agents** | Planner fixtures, Healer — починка устаревших селекторов |
| **Cline** | Не справился с большими файлами |
| **Continue.dev** | Минимальная ценность |

### Docker-окружение

- OrangeHRM 5.8.1 на Docker Desktop, ~1.5 GB RAM
- Миграция БД: 1 млн+ байт, 175 таблиц
- `Admin` / `Orangehrm@2026`

## Результаты

| Метрика | Значение |
|---------|----------|
| Модулей покрыто | 16/16 |
| @local тестов | 82 |
| @smoke тестов | 66 |
| Smoke suite | 73/73 за 2.2 минуты |
| POM | 13 |
| Проектов в config | 5 |

## Инструменты

Playwright, TypeScript, POM, Playwright MCP, KISS Sorcar, Playwright Agents,
Docker, OrangeHRM 5.8.1, Allure TestOps
