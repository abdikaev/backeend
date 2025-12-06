# Docker Документация

Этот проект поддерживает запуск в контейнерах с использованием Docker и docker-compose.
Ниже описано, как работает контейнеризация и как запустить приложение.

---

# 1. Требования
- Docker установлен  
- Docker Compose установлен  

Проверить версии можно командами:

docker --version  
docker-compose --version

---

# 2. Dockerfile (Backend)

Файл Dockerfile описывает, как создаётся образ приложения:

- устанавливается Python  
- копируется проект  
- устанавливаются зависимости  
- запускается сервер  

Образ создаётся командой:

docker build -t courses-backend .

---

# 3. docker-compose.yml

Compose-файл позволяет запускать **несколько сервисов одновременно**:

- backend (Django)
- db (PostgreSQL)

Запуск всех сервисов:

docker-compose up --build

Завершение работы:

docker-compose down

---

# 4. Структура сервисов

## Backend
- запускается командами:
  python manage.py migrate  
  python manage.py runserver  

## Database
- использует PostgreSQL
- данные сохраняются в volume

---

# 5. Запуск проекта в Docker

Полный запуск:

1) Собрать и запустить контейнеры:
docker-compose up --build

2) Открыть в браузере:
http://127.0.0.1:8000

---

# 6. Полезные команды

Посмотреть логи:
docker-compose logs -f

Перезапустить сервис:
docker-compose restart backend

Удалить образы и контейнеры:
docker system prune -a

---

# Примечание

Конфигурация может отличаться в зависимости от того,
какие именно сервисы вы добавите в docker-compose.yml.

