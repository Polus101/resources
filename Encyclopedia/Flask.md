# Запуск сайта в Repl

Чтобы выдать пользователю страничку «Hello, World!», нужно запустить этот небольшой кусочек кода:
```python3
from flask import Flask


def hello_world():
    return "Hello, World!"

app = Flask(__name__)
app.add_url_rule('/', 'hello', hello_world)
app.run('0.0.0.0')
```

# Что в нём происходит?

Строка `app = Flask(__name__)` создаёт приложение Flask. Это как бы макет сайта, который мы будем запускать.

На строке `app.add_url_rule('/', 'hello', hello_world)` мы говорим приложению, что если пользователь приходит на главную (`/`), нужно запустить функцию `hello_world`. `/` — главная сайта. Например, у сайта `vk.com` главная — это `/`, а страница с сообщениями по ссылке `vk.com/im` — это `/im`.

`hello` посередине — это название страницы. Можете называть её как угодно, вы создаёте это название для своего удобства.

Строка `app.run('0.0.0.0')` запускает сайт.

# В Repl появится встроенный браузер:
![sample text](https://dvmn.org/filer/canonical/1553247199/72/)

# А если хочу отправить файл?

Откройте его и верните его содержимое. Работает так:
```python3
from flask import Flask


def hello_world():
    with open('my_file.txt') as file:
      return file.read()

app = Flask(__name__)
app.add_url_rule('/', 'hello', hello_world)
app.run('0.0.0.0')
```
