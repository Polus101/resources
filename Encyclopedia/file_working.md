# Работа с файлами в Python

Стандартный синтаксис открытия файла:
```Python
with open("myfile.txt", "r") as my_file:
  file_contents = my_file.read()
print(file_contents)
```

На экране мы увидим содержимое файла `my_file.txt`. Таким образом в переменнйо `file_contents` будет лежать строка с содержимым файла. Аргумент `r` метода `open()` означает, что открываем файл в режиме read - для чтения

### Работа с кодировкой
Если мы хотим открыть файл с определенной кодировкой, достаточно лишь указать аргумент `encoding` в методе `open()`: 

```Python
with open("myfile.txt", "r", encoding="ваша кодировка") as my_file:
  file_contents = my_file.read()
print(file_contents)
```

## Работа с json файлами
Как и говорилось, в переменной file_contents лежит **строка** с содержимым файла. Чтобы эту строку превратить в списки и словари и работать с ними в дальнейшем, понадобится модуль json. 
Его не нужно дополнительно устанавливать, он входит в стандартный набор библиотек:

```Python
import json

with open("myfile.json", "r", encoding="ваша кодировка") as my_file:
  file_contents = my_file.read()

file_contents = json.loads(file_contents)
```

## Сохранение файла
По уроку вам это не понадобится, но может понадобится в жизни в будущем.
Для записи в файл нужно лишь указать режим w (write) и использовать не .read(), а .write():

```Python
my_text = "Хочу записать эту строку в файл"
with open("myfile.txt", "w") as my_file:
  my_file.write(my_text)
```





