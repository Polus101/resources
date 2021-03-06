# Про функции - просто

Тут все просто - функции как макросы в играх - нажал одну кнопку, а утебя произошло сразу много действий. 
Тоже и в программировании - запустил (вызвал) функцию одной строчкой кода, а выполнилось сразу много действи

```Python
def my_dunction(): #Создание функции
  print("Привет")
  a = 5
  b = 10
  print(a + b)
  
 my_function() # Вызов функции
```

На экране мы увидим
```
Привет
15
```

Это удобно, когда похожие или одни и те же действия необходимо делать на протяжении всего кода. 

### Например, у вас игра
Вам необходимо отрисовывать на экране спрайты игры. Спрайтов много. 
Отрисовывать их надо при разных условиях (На одном уровне одни, на другом другие; Когда игрок собирает предмет, предмет отрисовывать больше не надо и тд.)
Вместо того, чтобы каждый раз писать код, который отрисовывает спрайт на экране (а он скорее всего будет занимать не одну строчку кода - это сложный процесс) - можно создать функцию.
И отрисовывать нужный спрайт одной строчкой кода. Например `render_sprite()`

Чтобы ваша функциия знала, какой именно спрайт ей отрисовывать, нужно ей это указать. Для таких подсказок существуют **Аргументы** - `render_sprite(Player)`. Дальше подробннее

## Приммеры
Функцкия, которая возводит число во вторую степень
```Python
def sqare(a): #Создание функции
  sqare_number = a * a
  return sqare_number
  
print(sqare(5)) #Вызов функции
```

На экране получим число `25`.
Мы подсказали функции, что возводить в степень надо именно число 5. Число 5 запишется в переменную `a`, внутри функции переменная `a` умножится сама на себя и запишется в переменную `sqare_number`
А переменная вернется. (return). Вернется - значит, что выражение `sqare(5)` будет равносильна `25`. Тоесть для питона будет без разницы, напишем мы просто `25` или `sqare(5)`. Они для него будут равны.
Это будет удобно в дальнейшем для вычислений


### Правила
Правила простые:
- Функция ничего не должна принтить
- Не должна использовать переменные, которые создаются не в ней
- Переменные извне необходимо передавать аргументами:
```Python
def sqare(a): #Создание функции
  sqare_number = a * a
  return sqare_number

abc = 10
print(sqare(abc)) #Вызов функции
```
- Результат своей работы должна возвращать - `return`
