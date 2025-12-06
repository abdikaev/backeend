# CI/CD Документация

Проект использует GitHub Actions для автоматической сборки, тестирования
и проверки корректности кода при каждом коммите в репозиторий.

---

# 1. Что такое CI/CD

**CI (Continuous Integration)** — автоматическая проверка проекта при каждом изменении.

**CD (Continuous Deployment/Delivery)** — автоматический деплой или сборка проекта.

GitHub Actions позволяет запускать эти процессы без ручной работы.

---

# 2. Где находится конфигурация

Файлы workflow хранятся в папке:

.github/workflows/

Например:
main.yml  
tests.yml

---

# 3. Что делает CI

Обычно workflow выполняет такие действия:

1. Загружает код из GitHub  
2. Устанавливает Python  
3. Устанавливает зависимости  
4. Запускает тесты  
5. Проверяет стиль кода  
6. (опционально) собирает Docker-образ  

Пример:

- name: Install dependencies  
- name: Run tests  

---

# 4. Пример CI-конфигурации

```yaml
name: Django CI

on:
  push:
    branches: ["main"]
  pull_request:

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v3

      - name: Set up Python
        uses: actions/setup-python@v4
        with:
          python-version: 3.10

      - name: Install dependencies
        run: pip install -r requirements.txt

      - name: Run migrations
        run: python manage.py migrate

      - name: Run tests
        run: python manage.py test

