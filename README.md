# api_final

## Описание
### :fire::fire::fire:API для социальной сети Yatube.:fire::fire::fire:

API создан с использованием Django REST Framework.
Данный API имеет следующие возможности:

* Получение списка всех постов с паджинацией и без неё
* Получение списка всех групп
* Получение списка всех комментариев определенного поста
* Получение информации о конкретном посте, группе или комментарии
* Для зарегестрированных пользователей:
  * Возможность добавлять, изменять и удалять свои посты и комментарии
  * Возможность подписаться на другого пользователя
  * Возможность посмотреть, подписаны ли вы на определнного пользователя

## Установка на локальной машине

1. Клонировать репозитарий и перейти в получившийся каталог:
```
git clone https://github.com/RiteHist/api_final_yatube.git
```
```
cd api_final_yatube
```
2. Создать и активировать виртуальное окружение:
```
python -m venv env
```
```
source env/bin/activate
```
3. Установить зависимости:
```
python -m pip install --upgrage pip
```
```
pip install -r requirements.txt
```
4. Перейти в каталог yatube_api и выполнить миграции:
```
cd yatube_api
```
```
python manage.py migrate
```
5. Запустить проект:
```
python manage.py runserver
```

## Примеры запросов
### 1. Получение токена:
 * Путь:
  ```
  api/v1/jwt/create/
  ```
  * Метод POST
  * Payload:
  ```
  Content type: application/json
  {
    "username": "string",
    "password": "string"
  }
  ```
  * Возвращаемое значение:
  ```
  {
   "refresh": "string",
   "access": "string"
  }
  ```
### 2. Получение пяти постов после первого:
 * Путь:
 ```
 api/v1/posts/?limit=5&offset=1
 ```
 * Метод GET
 * Возвращаемое значение:
 ```
 {
    "count": 7,
    "next": "http://localhost:8000/api/v1/posts/?limit=5&offset=6",
    "previous": "http://localhost:8000/api/v1/posts/?limit=5",
    "results": [
        {
            "id": 2,
            "author": "me",
            "text": "test2",
            "pub_date": "2022-05-18T01:22:57.343014Z",
            "image": null,
            "group": null
        },
        {
            "id": 3,
            "author": "me",
            "text": "test3",
            "pub_date": "2022-05-18T01:23:00.448773Z",
            "image": null,
            "group": null
        },
        {
            "id": 4,
            "author": "me",
            "text": "test4",
            "pub_date": "2022-05-18T01:23:02.640036Z",
            "image": null,
            "group": null
        },
        {
            "id": 5,
            "author": "me",
            "text": "test5",
            "pub_date": "2022-05-18T01:23:04.676365Z",
            "image": null,
            "group": null
        },
        {
            "id": 6,
            "author": "me",
            "text": "test6",
            "pub_date": "2022-05-18T01:23:07.004191Z",
            "image": null,
            "group": null
        }
    ]
}
```
