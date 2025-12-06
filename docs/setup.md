# Установка и запуск проекта

## 1. Клонирование репозитория
Скачайте проект из GitHub:

git clone <[URL вашего репозитория](https://github.com/abdikaev/backeend.git)>
cd backeend

## 2. Создание виртуального окружения
Создайте и активируйте виртуальное окружение:

python -m venv venv

Если вы на Windows:
venv\Scripts\activate

Если вы на macOS/Linux:
source venv/bin/activate

## 3. Установка зависимостей
Установите все библиотеки:

pip install -r requirements.txt

## 4. Применение миграций
Создайте таблицы в базе данных:

python manage.py migrate

## 5. Создание администратора
Чтобы зайти в админку, создайте суперпользователя:

python manage.py createsuperuser

## 6. Запуск сервера
Запустите проект командой:

python manage.py runserver

После запуска откройте браузер и перейдите по адресу:
http://127.0.0.1:8000
