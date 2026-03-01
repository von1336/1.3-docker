# Домашнее задание 1.3 — Docker

## Задание 1: Nginx с кастомной страницей

- Образ nginx с заменённой страницей приветствия в `/usr/share/nginx/html`.
- Запуск: `docker build -t my-nginx . && docker run -p 8080:80 my-nginx`
- Открыть: http://localhost:8080

## Задание 2: REST API (Django + SQLite) в контейнере

- Backend на Django REST с SQLite (без зависимости от PostgreSQL).
- Конфигурация через переменные окружения.
- Запуск см. в `backend/README.md`.
