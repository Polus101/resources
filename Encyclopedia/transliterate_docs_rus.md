# Библиотека transliterate

Транслитерация — точная передача знаков одной письменности знаками другой письменности. Например, английское `Hello` транслитируется в русское `Хелло`.

Библиотека поддерживает разные языки с помощью языковых пактов. В комплекте с библиотекой идут следущие языковые пакеты:

* Armenian
* Bulgarian (beta)
* Georgian
* Greek
* Macedonian (alpha)
* Mongolian (alpha)
* Russian
* Serbian (alpha)
* Ukrainian (beta)

Библиотека предоставляет несколько полезных инструментов:

* Простой генератор [lorem ipsum](https://ru.wikipedia.org/wiki/Lorem_ipsum) для выбранных языков.
* Распознание языка, на котором написан текст (если есть нужный языковой пакет).
* Функция `slugify` (перевод `some sample text here` в `some-sample-text-here`).

# С чего начать

Так можно получить список доступных языков на компьютере:
```python
from transliterate import get_available_language_codes


print(get_available_language_codes())  # Выведет ['el', 'hy', 'ka', 'ru']
```
А вот пример использования основного функционала:
```python
from transliterate import translit


print(translit("Lorem ipsum dolor sit amet", 'hy'))  # Выведет Լօրեմ իպսում դօլօր սիտ ամետ
print(translit("Lorem ipsum dolor sit amet", 'ka'))  # Выведет ლორემ იპსუმ დოლორ სით ამეთ
print(translit("Lorem ipsum dolor sit amet", 'uk'))  # Выведет Лорем іпсум долор сіт амет
```

Первый аргумент — переводимый текст, а второй — код языка.
