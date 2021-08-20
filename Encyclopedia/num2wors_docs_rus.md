# Библиотека num2words — перевод чисел в слова

`num2words` — библиотека, которая переводит числа (например, 42) в слова (сорок два) или даже в порядковые числительные (сорок второй).

Очень проста в использовании:
```python
from num2words import num2words

print(num2words(42))  # Выведет forty-two
print(num2words(42, to='ordinal')) # Выведет forty-second
print(num2words(42, lang='fr'))  # Выведет quarante-deux
```

Помимо основного аргумента-числа есть необязательные, дополнительные аргументы:

* Аргумент **to** может принимать следущие значения:
    * `"cardinal"` — просто перевод в число: `2019` —> `two thousand and nineteen`.
    * `"ordinal"` — перевод в порядковое числительное: `2019` —> `two thousand and nineteenth`.
    * `"ordinal_num"` — оставить числом: `2019` —> `2019th`.
    * `"year"` — в год: `2019` —> `twenty nineteen`
    * `"currency"` — в евро: `2019` —> `twenty euro, nineteen cents`

* **lang** — определяет в какой язык переводить:
   - `"en"` (English, default)
   - `"ar"` (Arabic)
   - `"cz"` (Czech)
   - `"de"` (German)
   - `"dk"` (Danish)
   - `"en_GB"` (English - Great Britain)
   - `"en_IN"` (English - India)
   - `"es"` (Spanish)
   - `"es_CO"` (Spanish - Colombia)
   - `"es_VE"` (Spanish - Venezuela)
   - `"eu"` (EURO)
   - `"fi"` (Finnish)
   - `"fr"` (French)
   - `"fr_CH"` (French - Switzerland)
   - `"fr_BE"` (French - Belgium)
   - `"fr_DZ"` (French - Algeria)
   - `"he"` (Hebrew)
   - `"id"` (Indonesian)
   - `"it"` (Italian)
   - `"ja"` (Japanese)
   - `"ko"` (Korean)
   - `"lt"` (Lithuanian)
   - `"lv"` (Latvian)
   - `"no"` (Norwegian)
   - `"pl"` (Polish)
   - `"pt"` (Portuguese)
   - `"pt_BR"` (Portuguese - Brazilian)
   - `"sl"` (Slovene)
   - `"sr"` (Serbian)
   - `"ro"` (Romanian)
   - `"ru"` (Russian)
   - `"sl"` (Slovene)
   - `"tr"` (Turkish)
   - `"th"` (Thai)
   - `"vi"` (Vietnamese)
   - `"nl"` (Dutch)
   - `"uk"` (Ukrainian)


Некоторые коды состоят из языка и страны: `fr_FR`. Если страна не поддерживается, но поддерживается язык, то программа использует код языка: `fr`. Если вы используете язык не из этого списка, получите `NotImplementedError`.