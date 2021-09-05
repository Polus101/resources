# Библиотека urwid

Библиотека `urwid` позволяет создавать пользовательские меню внутри терминала. В этой документации мы подробно рассмотрим побуквенный перехват пользовательского ввода. [Оригинальная документация здесь](http://urwid.org/tutorial/index.html)

# Посимвольный перехват ввода

`urwid` позволяет получать данные от пользователя прямо по мере того, как он печатает:

![sample text](http://urwid.org/_images/sig1.png) ![sample text](http://urwid.org/_images/sig2.png) ![sample text](http://urwid.org/_images/sig3.png) ![sample text](http://urwid.org/_images/sig4.png)

Для примера приведём исходный код программы, использующей эту функцию:

```python3
import urwid

def on_ask_change(edit, new_edit_text):
    reply.set_text("Вы тайно написали: %s" % new_edit_text)

ask = urwid.Edit('Тайный ввод: ', mask='*')
reply = urwid.Text("")
menu = urwid.Pile([ask, reply])
menu = urwid.Filler(menu, valign='top')
urwid.connect_signal(ask, 'change', on_ask_change)
urwid.MainLoop(menu).run()
```

- Переменная `ask` отвечает за вопрос, который будет выведен в начале.
- Переменная `reply` отвечает за место, где будет размещён ответ на ваш ввод.
- `menu` — это всё то, что будет выведено на экран. Туда мы кладём `ask` и `reply`. На следущей строчке мы заставляем меню прикрепиться к верху терминала.
- `urwid.connect_signal(ask, 'change', on_ask_change)` — прикрепляет коллбэк `on_ask_change` к изменению текста в поле `ask`. Как только пользователь напишет какой-либо текст в поле `ask` — вызовется коллбэк `on_ask_change`.
- `urwid.MainLoop(menu).run()` — запускает бесконечный цикл, который не даёт программе завершиться.
