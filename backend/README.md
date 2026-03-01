# Backend (Django REST + SQLite) в Docker

## Переменные окружения

- `DJANGO_SECRET_KEY` — секретный ключ (по умолчанию dev-ключ).
- `DJANGO_DEBUG` — 0/1 или false/true.
- `DJANGO_ALLOWED_HOSTS` — хосты через запятую (например, `*` для теста).
- `DJANGO_DB_PATH` — путь к файлу SQLite (по умолчанию `db.sqlite3` в проекте).

## Сборка и запуск контейнера

```bash
docker build -t backend .
docker run -p 8000:8000 -e DJANGO_ALLOWED_HOSTS="*" backend
```

Перед сборкой нужно выполнить миграции. В Dockerfile можно добавить шаг миграций, либо выполнить их при первом запуске через entrypoint. Для простоты миграции выполняются при старте через команду:

При старте контейнера автоматически выполняются миграции, затем запускается Gunicorn.

## Проверка API

- GET http://localhost:8000/api/items/ — список объектов
- POST http://localhost:8000/api/items/ — создание (тело JSON: `{"name": "...", "description": "..."}`)
- GET/PUT/PATCH/DELETE http://localhost:8000/api/items/{id}/