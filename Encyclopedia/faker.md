# Библиотека Faker

Faker — библиотека для генерации фальшивых данных. Подходит на все случаи жизни: тестирование кода, заполнение баз данных для стресс-тестов, анонимизация данных. Для всего этого используют Faker.

# Пример использования


```python3
from faker import Faker

fake = Faker("ru_RU")
print(fake.name())
```

Сперва мы импортируем библиотеку, затем объявляем генератор фальшивых данных и кладём в переменную `fake`. Генератор создаём с поддержкой русского языка. Для этого указываем `"ru_RU"`.

На последней строчке выводится случайное ФИО, например: `Тарасова Наина Вениаминовна`.

# Что можно сгенерировать

Данные генерируются с учётом выбранной страны. Ниже приведены примеры для `"ru_RU"` (России).

Набор доступных методов зависит от языка. Для кода `en`, например, можно генерировать названия военных баз, а почтовые коды не шестизначные, как в России, а пятизначные, как в Америке. Полный перечень [здесь](https://faker.readthedocs.io/en/latest/providers.html).

## Адреса

| Название | Метод | Пример |
| :------------- | :----- | :----- |
| Индекс | fake.postcode() | 875746 |
| Название улицы | fake.street_name() | ул. Прудовая |
| Адрес на улице | fake.street_address() | ул. Балтийская, д. 23 |
| Суффикс улицы | fake.street_suffix() | ул. |
| Название страны | fake.country() | Suriname |
| Название города | fake.city() | Самара |
| Полный адрес | fake.address() | к. Приозерск, ул. Урицкого, д. 98, 713715 |

## Имена

| Название | Метод | Пример |
| :------------- | :----- | :----- |
| ФИО | fake.name() | Тарасова Наина Вениаминовна |
| Мужское ФИО | fake.name_male() | Кудряшов Платон Елизарович |
| Женское ФИО | fake.name_female() | Архипова Марфа Вадимовна |
| Фамилия | fake.last_name() | Селиверстов |
| Мужская Фамилия | fake.last_name_male() | Ширяев |
| Женская Фамилия | fake.last_name_female() | Кудряшова |
| Имя | fake.first_name() | Венедикт |
| Мужское Имя | fake.first_name_male() | Пантелеймон |
| Женское Имя | fake.first_name_female() | Фаина |
| Женский Префикс | fake.prefix_female() | г-жа |
| Мужской Префикс | fake.prefix_male() | тов. |

## Дополнительные методы

| Название | Метод | Пример |
| :------------- | :----- | :----- |
| Профессия | fake.job() | Нейрохирург |
| Номер телефона | fake.phone_number() | +78415389555 |
| Сайт | fake.hostname() | web-59.rao.net |
| Почта | fake.ascii_free_email() | ladimir24@mail.ru |
| Ссылка | fake.uri() | http://www.zhuravlev.biz/blog/main/main/ |
| Компания | fake.company() | РАО «Суворова Мельников» |