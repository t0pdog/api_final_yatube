### Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/t0pdog/api_final_yatube.git
```

```
cd api_final_yatube
```

Cоздать и активировать виртуальное окружение:

```
python -m venv venv
```

```
source venv/Scripts/activate
```

```
python -m pip install --upgrade pip
```

Установить зависимости из файла requirements.txt:

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

По адресу ниже доступна документация в формате redoc:

```
http://127.0.0.1:8000/redoc/
```

Вот некоторые примеры запросов к эндпоинтам и их ответы:


Получить список всех публикаций. При указании параметров
limit и offset выдача должна работать с пагинацией. ( GET запрос):

```
http://127.0.0.1:8000/api/v1/posts/
```

Ответ сервера:
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

Добавление новой публикации в коллекцию публикаций. 
Анонимные запросы запрещены. ( POST запрос):

```
http://127.0.0.1:8000/api/v1/posts/
```
В теле запроса передаем параметры, для создания публикации:
```

{
  "text": "string",
  "image": "string",
  "group": 0
}
```

Возможные ответы сервера:
```

201 Удачное выполнение запроса:
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

400 Отсутствует обязательное поле в теле запроса:
```

{
  "text": [
    "Обязательное поле."
  ]
}
```

401 Запрос от имени анонимного пользователя:
```

{
  "detail": "Учетные данные не были предоставлены."
}