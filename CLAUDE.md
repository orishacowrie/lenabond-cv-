# CLAUDE.md — правила работы с этим репозиторием

Это CV-сайт lenabond.com (Lena Bondareva). Деплой: Vercel, авто-деплой при push в main (~1-2 мин). Домен на Cloudflare.

## Структура — что есть что

- `cv/hrbp/` — резюме Senior HR Business Partner
- `cv/hrd/` — резюме HR Director
- `cv/hr-projects/` — резюме HR Projects (RU/EN toggle)
- `cv/ta-lead/` — резюме TA Lead
- `cv/ta-head/` — резюме Head of Talent Acquisition
- `quiz/` — HR AI Maturity Quiz, ОТДЕЛЬНЫЙ проект. Не трогать при работе с резюме.
- `1test/` — отдельная рабочая папка. Не трогать при работе с резюме.

## Git-дисциплина (ОБЯЗАТЕЛЬНО)

1. ПЕРВОЕ действие в любой сессии: `git pull --no-rebase` — с этим репо работают и из обычного терминала, и из Claude Code, состояние могло уйти вперёд.
2. Перед КАЖДЫМ `git push`: сначала `git pull --no-rebase`.
3. Если git хочет открыть редактор для merge-сообщения: использовать `git commit --no-edit`. Vim не открывать.
4. НИКОГДА не коммитить и не пушить без явного подтверждения пользователя. Сначала показать diff, дождаться «да».
5. Не трогать файлы вне текущей задачи.
6. В конце сессии перечислить ушедшие в main коммиты, по одной строке.

## Правила файлов и папок

- Имена папок: только нижний регистр, дефисы, БЕЗ пробелов (был баг 404 из-за папки "cv/ ta-lead" с пробелом).
- Страницы резюме строго называются `index.html` внутри своей папки.

## Правила контента резюме (НЕ НАРУШАТЬ)

- Ничего не выдумывать. Все факты только из подтверждённых источников.
- Inktech НИКОГДА не называть по имени — только «IT holding: AI products, fintech, entertainment-tech».
- Dyninno: November 2024 — September 2025 (на hrbp и hrd осознанно оставлен December 2024).
- Dyninno-тайтл: «Recruitment Head» на ta-lead, «Global Recruitment Head» на ta-head.
- Severstal: September 2024 — November 2024.
- Beeline: профессиональный + IT найм (НЕ массовый), 44M+ клиентов (НЕ 58M).
- OPEN Group: на ta-lead/ta-head короткая запись; полная — на hrd/hrbp. Только польский аффилиат, 15,000+ field workforce.
- Tools на всех страницах: Asana · Bitrix · Monday.com · Trello · Sage ATS · [Sana только на HRD] · GitHub · Vercel · Cloudflare · Supabase · Claude Code. НЕ добавлять Cursor и «AI Tools».
- About заканчивается фразой: «I tinker with Claude Code. Sometimes it even works.»
- Языки: English — C1 · Russian — native · German — A2 (B1 by year end, I promise 😅).
- Курс «Driver-Based Headcount Planning, 2026» — на hrd, первым в списке Courses.
- Результаты OPEN: +19% revenue, +49% profit per headcount, attrition 33→28%, internal promotions 27→37%, engagement 76→81%.
- Результаты Beeline: recruiter productivity 4.1→6.3, 8,000+ ролей упоминается только на ta-head, attrition 50→30%.

## PDF-версии

Светлая тема, одна колонка, A4. Генерация: Playwright — `pg.emulate_media(media='print')`, `pg.pdf(format='A4', print_background=True, prefer_css_page_size=True)`. Поля `@page 16mm 14mm`. Правила вёрстки: заголовок роли не отрывается от тела (page-break-inside: avoid на .job-header), pill-блоки и About неразрывны. Светлый HTML собирается отдельным файлом, фото инжектится из base64 (можно вытащить из любой cv-страницы).
