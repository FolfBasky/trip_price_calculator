# TripCost — калькулятор стоимости поездки

Веб-приложение для расчёта стоимости автомобильной поездки: топливо, амортизация, ТО, страховка, налог, платные дороги, история поездок и экспорт отчёта в PDF/печать.

## Возможности

- построение маршрута на карте;
- расчёт стоимости поездки по автомобилю и типу топлива;
- выбор расхода: заводской, реальный, средний по сообществу;
- сохранение собственных замеров расхода;
- история поездок пользователя;
- экспорт отчёта с картой и маршрутом;
- регистрация и авторизация пользователей.

## Стек

- Backend: Python, FastAPI, SQLAlchemy, SQLite;
- Frontend: HTML, CSS, JavaScript, Leaflet;
- Карты: OpenStreetMap;
- Маршруты/геокодинг: backend-proxy к внешним сервисам.

## Быстрый запуск

### Windows

```bat
start.bat
```

### Linux/macOS

```bash
chmod +x run.sh
./run.sh
```

После запуска откройте:

```text
http://localhost:8080
```

## Ручной запуск

```bash
cd backend
python -m venv .venv
```

Windows:

```bat
.venv\Scripts\activate
pip install -r requirements.txt
python -m uvicorn main:app --host 0.0.0.0 --port 8080 --reload
```

Linux/macOS:

```bash
source .venv/bin/activate
pip install -r requirements.txt
python -m uvicorn main:app --host 0.0.0.0 --port 8080 --reload
```

## Настройки окружения

Можно создать `.env` на основе `.env.example` или передать переменные окружения вручную.

| Переменная | Назначение | Значение по умолчанию |
|---|---|---|
| `SECRET_KEY` | ключ подписи JWT | dev-ключ из кода |
| `DATABASE_URL` | строка подключения SQLAlchemy | SQLite-файл `backend/trip_calculator.db` |

Для локальной разработки значения по умолчанию подходят. Для продакшена обязательно задайте свой `SECRET_KEY`.

## Docker

```bash
docker compose up --build
```

Приложение будет доступно на `http://localhost:8080`.

## Подготовка к публикации на GitHub

В репозиторий не нужно добавлять:

- `.venv/`;
- `__pycache__/`;
- `*.db`;
- `.env`;
- временные ZIP/RAR-архивы.

Это уже учтено в `.gitignore`.

## Структура проекта

```text
trip-calculator/
├── backend/
│   ├── main.py
│   ├── models.py
│   ├── schemas.py
│   ├── auth.py
│   ├── database.py
│   ├── fuel_service.py
│   ├── seed.py
│   └── requirements.txt
├── frontend/
│   ├── index.html
│   ├── styles.css
│   └── js/
├── .github/workflows/ci.yml
├── Dockerfile
├── docker-compose.yml
├── run.sh
├── start.bat
└── README.md
```

## Лицензия

MIT. См. файл `LICENSE`.
