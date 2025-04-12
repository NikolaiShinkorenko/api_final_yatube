# api_final_yatube

## Описание проекта
Финальная версия API для социальной сети YaTube, который позволяет:
- Получать списки публикаций, комментариев, групп
- Получать публикации, комментарии, информацию о сообществе по id
- Создавать, удалять и обновлять (в том числе частично) публикации и комментарии к ним
- Подписываться на авторов и получать список подписок

Для аутентификации используются JWT-токены.

## Использованные технологии
- Python 3.10.11
- Django 5.2 
- Django REST Framework 3.16.0
- Simple JWT + Djoser

## Как запустить проект

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/NikolaiShinkorenko/api_final_yatube.git
```

```
cd api_final_yatube
```

Cоздать и активировать виртуальное окружение:

```
python -m venv venv
```

```
source venv/Script/activate
```

Установить зависимости из файла requirements.txt:

```
python -m pip install --upgrade pip
```

```
pip install -r requirements.txt
```

Выполнить миграции:

```
python manage.py migrate
```

Запустить проект:

```
python manage.py runserver
```

## Примеры запросов

### Запрос JWT токена с использованием логина и пароля

POST .../api/v1/jwt/create
```
{
    "username": "User",
    "password": "password123"
}
```

Ответ:
```
{
  "refresh": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0b2tlbl90eXBlIjoicmVmcmVzaCIsImV4cCI6MTc0NDUzNTU4OCwiaWF0IjoxNzQ0NDQ5MTg4LCJqdGkiOiI1YzEzMmZhYTVhZDI0ZTY0YWNmODQ1YTEzZjlkZmQwZCIsInVzZXJfaWQiOjF9.4YXfGEcV7NDbzsp45-BdRaU2MDT1MEc7WbRE2gHLkWY",
  "access": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNzQ0NTM1NTg4LCJpYXQiOjE3NDQ0NDkxODgsImp0aSI6IjFhMzA3ZTM5Y2NlODRjNjZhMDQ2MDc0MjhhMmZjMzRhIiwidXNlcl9pZCI6MX0.6zqvrY_knM17zlUKmtUgvyRAAv5rekuKyz4Bnz7j7Wo"
}
```

### POST-запрос с токеном: добавление новой публикации

POST .../api/v1/posts/

```
{
    "text": "string",
    "group": 1
}
```

Ответ:
```
{
    "id": 2,
    "author": "User",
    "text": "string",
    "pub_date": "2025-04-12T09:28:24.582341Z",
    "image": null,
    "group": 1
}
```

### GET-запрос с токеном: получаем информацию о группе 
GET .../api/v1/groups/1/

Ответ:
```
{
    "id": 1,
    "title": "GroupTitle",
    "slug": "group-slug",
    "description": "Test group for api_final_yatube"
}
```

### POST-запрос с токеном: подписка авторизованного пользователя на автора
POST .../api/v1/follow/
```
{
    "following": "Author"
}
```

Ответ:
```
{
    "id": 1,
    "user": "User",
    "following": "Author"
}
```

## Автор
GitHub: [NikolaiShinkorenko](https://github.com/NikolaiShinkorenko)