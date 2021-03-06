# Что такое переменная в Python
Переменные — это способ сохранить в памяти компьютера данные

Например:
```python3
x = "Данил"
print(x)
```
В консоли выведется:
```
Данил
```

В этом примере мы создали перемемнную `x` и положили в нее `"Данил"`.
Когда код запустится, он подставит в `print(x)`  `"Данил"` вместо `x`.
Тут как в школьной математике, где мы писали x = 7. Только в программировании в переменную можно пололжить почти что угодно)

## Зачем они нужны
Переменные удобны, когда одно значение используется многократно:
```python3
x = 20

print('Цена штуки', x)
print('Цена десятка', 10 * x)
print('Цена дюжины', 12 * x)
```

Или когда нужно выполнить много действий подряд. Когда мы делаем всё сразу в одной строчке, становится немного непонятно:
```python3
print("Сказка о том, как %зверь% съел %еда%. Жил был %зверь% в своей %дом% и ел %еда%. Конец.".replace("%зверь%","кролик").replace("%дом%", "норке").replace("%еда%", "морковку"))
```

Этот код выводит:
```
Сказка о том, как кролик съел морковку. Жил был кролик в своей норке и ел морковку. Конец.
```

Переменные позволяют разделить код на несколько строк:
```python3
sample = "Сказка о том, как %зверь% съел %еда%. Жил был %зверь% в своей %дом% и ел %еда%. Конец."
sample = sample.replace("%зверь%","кролик")
sample = sample.replace("%дом%", "норке")
sample = sample.replace("%еда%", "морковку")
```
