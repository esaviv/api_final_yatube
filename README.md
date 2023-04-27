# REST API для сервиса Yatube
## Описание
Социальная сеть блогеров. В ней пользователи могут создать учетную запись, публиковать записи, подписаться на любимых авторов и отмечать понравившиеся записи.
### Технологии
Python 3.9, Django 2.2.19, Django REST Framework 3.12.4, djoser 2.1.0

## Автор
esaviv

## Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/esaviv/api_yatube
```

```
cd api_yatube
```

Cоздать и активировать виртуальное окружение:
```
python3 -m venv venv | python -m venv venv
```
```
source venv/bin/activate | source venv/Scripts/activate
```
```
python3 -m pip install --upgrade pip | python -m pip install --upgrade pip
```
Установить зависимости из файла requirements.txt:
```
pip install -r requirements.txt
```
Выполнить миграции:
```
python3 yatube_api/manage.py migrate | python yatube_api/manage.py migrate
```
Запусти
```
python3 yatube_api/manage.py runserver | python yatube_api/manage.py runserver
```

## Примеры запросов и ответов:

### Получить JWT-токен
#### POST
```
/api/v1/jwt/create/
```
```
{
  "user": "string",
  "password": "string"
}
```
Ответ:
```
{
  "refresh": "string",
  "access": "string"
}
```


### Создание публикации
#### POST
```
/api/v1/posts/
```
```
{
  "text": "string",
  "image": "string",
  "group": 0
}
```
Ответ:
```
{
  "id": 0,
  "author": "string",
  "text": "string",
  "pub_date": "2019-08-24T14:15:22Z",
  "image": "string",
  "group": 0
}
```

### Получение публикаций
#### GET
```
/api/v1/posts/
```
Ответ:
```
{
  "count": 123,
  "next": "http://api.example.org/accounts/?offset=400&limit=100",
  "previous": "http://api.example.org/accounts/?offset=200&limit=100",
  "results": [
    {
      "id": 0,
      "author": "string",
      "text": "string",
      "pub_date": "2021-10-14T20:41:29.648Z",
      "image": "string",
      "group": 0
    }
  ]
}
```

### Получение публикации
#### GET
```
/api/v1/posts/{id}/
```
Ответ:
```
{
  "id": 0,
  "author": "string",
  "text": "string",
  "pub_date": "2019-08-24T14:15:22Z",
  "image": "string",
  "group": 0
}
```


### Добавление комментария
#### POST
```
/api/v1/posts/{post_id}/comments/
```
```
{
  "text": "string"
}
```
Ответ:
```
{
  "id": 0,
  "author": "string",
  "text": "string",
  "created": "2019-08-24T14:15:22Z",
  "post": 0
}
```

### Получение комментариев
#### GET
```
/api/v1/posts/{post_id}/comments/
```
Ответ:
```
[
  {
    "id": 0,
    "author": "string",
    "text": "string",
    "created": "2019-08-24T14:15:22Z",
    "post": 0
  }
]
```

### Получение комментария
#### GET
```
/api/v1/posts/{post_id}/comments/{id}/
```
Ответ:
```
{
  "id": 0,
  "author": "string",
  "text": "string",
  "created": "2019-08-24T14:15:22Z",
  "post": 0
}
```


### Список сообществ
#### GET
```
/api/v1/groups/
```
Ответ:
```
[
  {
    "id": 0,
    "title": "string",
    "slug": "string",
    "description": "string"
  }
]
```


### Подписка
#### POST
```
/api/v1/follow/
```
Ответ:
```
{
  "following": "string"
}
```

### Подписки
#### GET
```
/api/v1/follow/
```
Ответ:
```
[
  {
    "user": "string",
    "following": "string"
  }
]
```
