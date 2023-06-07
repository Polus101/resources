# API Яндекс-геокодера
**Перед использованием получите API ключ в [кабинете разработчика](https://developer.tech.yandex.ru/services/)**

## Получение ключа - важное
- Выбираем JavaScript API и HTTP декоддер
- Название компании - Polus 101
- В открытой системе 
- В бесплатном проекте 
- Буду отображать данные на карте
- Ссылка на сайт - ссылка на репл
- Описание - в учебных целях
- Количество запросов - минимальное

## Использование
Готовая функция на основе API, которой вы будете пользоваться (для ее работы необходимо установить библиотеку requests версии 2):
```Python
import requests

def fetch_coordinates(apikey, address):
    base_url = "https://geocode-maps.yandex.ru/1.x"
    response = requests.get(base_url, params={
        "geocode": address,
        "apikey": apikey,
        "format": "json",
    })
    response.raise_for_status()
    found_places = response.json()['response']['GeoObjectCollection']['featureMember']

    if not found_places:
        return None

    most_relevant = found_places[0]
    lon, lat = most_relevant['GeoObject']['Point']['pos'].split(" ")
    return lon, lat
```

Пример ее использования:
```Python
apikey = '41f31cb9-8414-4c9a-bd82-79ec5d22b8ec'  # ваш ключ

coords = fetch_coordinates(apikey, "Внуково")
print(coords)  # ('37.295014', '55.608562')

coords = fetch_coordinates(apikey, "Серпуховская")
print(coords)  # ('37.624992', '55.726872')

coords = fetch_coordinates(apikey, "Красная площадь")
print(coords)  # ('37.621031', '55.753595')

coords = fetch_coordinates(apikey, "UNEXIST")
print(coords)  # None
```
## ЧАСТАЯ ОШИБКА
API Яндекса регистрирует новый ключ около получаса, так что первые пол часа может выдаваться ошибка `HTTPError: 403 Client Error: Forbidden for url ...`
