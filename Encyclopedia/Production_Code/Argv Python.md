# Использование аргументов командной строки в Python

Аргументы командной строки - это замена стандартного input для ввода пользовательских данных. Единственное отличие, что используя аргументы, пользователь вводит все данные сразу при запуске программы; а используя обычный input он вводит данные тогда, когда это задумал программист

Кажется, будто аргументы использовать неудобно по сравнению с input. Но бывают программы, в которых удобно сразу задать все данные и отправить программу работать, чем вводить данные постепенно.

Более того, если программа будет работать на сервере (например, майнер, рассылка или бот), то использование input будет недопустимым, так как и сервер может "повиснуть", если неправильно настроен, да и окно сервера забьется лишней информацией.

Поэтому в подобных программах от input программисты отказываются в пользу аргументов. Хотя они и посложнее будут)

**Аргументы указываются при запуске программы. Например, так:**

`python main.py --login qwerty --password 1234 --mode attack`

В этом примере три аргумента:
- login - равняется qwerty
- password - 1234
- mode - attack

## Как создать

**Импортируем библиотеку (не нуждается в установке)**
```python
import argparse
```

**Создаем переменную парсер**
```python
parser = argparse.ArgumentParser(
        description='Описание программы'
)
```
Здесь пишем свое описание программы - оно будет высвечиваться, если пользователь напишет в терминале `python main.py --help`.

**Создаем аргумент**
```python
parser.add_argument('--название аргумента', help='Описание, что нужно указывать в аргументе')
```
Здесь так же пишем описание аргумента - его пользователь тоже видит при вызове `python main.py --help`

Так же можно задать значение по умолчанию. Ему будет равен аргумент автоматически, если пользователь ничего не напишет в нем
```python
parser.add_argument('--название аргумента', help='Описание, что нужно указывать в аргументе', default='значение по умолчанию')
```

**И создаем переменную, в которой будет лежать то, что напишет пользователь в аргументе**
```python   
название переменной для аргумента = parser.parse_args().название аргумента
```


### Вот финальный результат
```python
import argparse

parser = argparse.ArgumentParser(
        description='Супер программа взлома пентагона'
)

parser.add_argument('--mode', help='Режим работы программы - attack или sleep', default='attack')

program_mode = parser.parse_args().mode

```





