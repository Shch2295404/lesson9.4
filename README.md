# lesson9.4
Introduction to the Flask framework for Web development / Знакомство с фреймворком Flask для веб-разработки

---

# Учебный проект на Flask

Этот репозиторий содержит два учебных задания, выполненных с использованием Flask. Каждое задание находится в отдельной папке: `task_1` и `task_2`.

---

## Задание 1: Отображение текущих даты и времени

### Описание
В этом задании создано простое Flask-приложение, которое отображает текущие дату и время на главной странице. Время обновляется при каждом запросе.

### Структура проекта
```
task_1/
├── main.py                # Основной файл Flask-приложения
└── templates/
    └── index.html        # HTML-шаблон для главной страницы
```

### Как запустить
1. Перейдите в папку `task_1`:
   ```bash
   cd task_1
   ```
2. Установите Flask, если он ещё не установлен:
   ```bash
   pip install flask
   ```
3. Запустите приложение:
   ```bash
   python main.py
   ```
4. Перейдите по адресу `http://127.0.0.1:5000` в браузере.

---

## Задание 2: Многостраничное Flask-приложение

### Описание
В этом задании создано многостраничное Flask-приложение с тремя страницами:
- **Главная страница** (`index.html`)
- **Блог** (`blog.html`)
- **Контакты** (`contacts.html`)

На всех страницах реализовано навигационное меню, которое работает при запуске проекта через Flask.

### Структура проекта
```
task_2/
├── main.py                # Основной файл Flask-приложения
└── templates/
    ├── index.html        # Главная страница
    ├── blog.html         # Страница блога
    └── contacts.html     # Страница контактов
```

### Как запустить
1. Перейдите в папку `task_2`:
   ```bash
   cd task_2
   ```
2. Установите Flask, если он ещё не установлен:
   ```bash
   pip install flask
   ```
3. Запустите приложение:
   ```bash
   python main.py
   ```
4. Перейдите по адресу `http://127.0.0.1:5000` в браузере.

---

## Рекомендации по оптимизации

### Использование шаблона `base.html`
Для упрощения поддержки и уменьшения дублирования кода в задании 2 рекомендуется использовать **наследование шаблонов** через `base.html`. Это позволит:
1. Вынести общие элементы (например, навигационное меню и футер) в один файл.
2. Упростить добавление новых страниц.
3. Уменьшить количество повторяющегося кода.

Пример структуры с `base.html`:
```
task_2/
├── main.py
└── templates/
    ├── base.html         # Базовый шаблон
    ├── index.html        # Наследует base.html
    ├── blog.html         # Наследует base.html
    └── contacts.html     # Наследует base.html
```

Пример `base.html`:
```html
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{% block title %}Мой сайт{% endblock %}</title>
    <link href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
        <a class="navbar-brand" href="{{ url_for('index') }}">Мой сайт</a>
        <div class="collapse navbar-collapse">
            <ul class="navbar-nav mr-auto">
                <li class="nav-item"><a class="nav-link" href="{{ url_for('index') }}">Главная</a></li>
                <li class="nav-item"><a class="nav-link" href="{{ url_for('blog') }}">Блог</a></li>
                <li class="nav-item"><a class="nav-link" href="{{ url_for('contacts') }}">Контакты</a></li>
            </ul>
        </div>
    </nav>

    <div class="container mt-5">
        {% block content %}{% endblock %}
    </div>

    <footer class="footer mt-auto py-3 bg-dark text-white text-center">
        <p>&copy; 2023 Мой сайт. Все права защищены.</p>
    </footer>
</body>
</html>
```

Пример использования в `index.html`:
```html
{% extends "base.html" %}

{% block title %}Главная страница{% endblock %}

{% block content %}
    <h1 class="display-4">Добро пожаловать на наш сайт!</h1>
    <p class="lead">Здесь вы найдёте полезную информацию и интересные статьи.</p>
{% endblock %}
```

---

## Заключение
Этот проект демонстрирует базовые возможности Flask для создания веб-приложений. Вы можете использовать его как основу для более сложных проектов.

---

