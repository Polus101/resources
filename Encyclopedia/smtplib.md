# Как отправить письмо с помощью SMTPlib

SMTP — Simple Mail Transfer Protocol (**Простой Протокол Передачи Почты**). Но слово *простой* совсем не значит, что есть *крутой*. SMTP — самый популярный протокол для отправки почты между серверами.

По итогу этого туториала вы сможете правильно оформить своё письмо и отправить его по почте.

## 1. Оформите письмо с помощью заголовков

Чтобы отправить письмо, ваша программа должна связаться с сервером почтового сервиса (Gmail, Yandex, Mail.ru и т.д.) и передать ему всю нужную информацию: кому, от кого, что в письме. Протокол устанавливает правила, как должно выглядеть такое сообщение:
```
From: Адрес отправителя
To: Адрес получателя
Subject: Заголовок письма
Content-Type: text/plain; charset="UTF-8";

Начало вашего текста ...
```

Например, если нужно отправить письмо `Привет!` с адреса `mymail@gmail.com` на адрес `friend@gmail.com` с заголовком `Важно!`, сообщение должно выглядеть так:
```
From: mymail@gmail.com
To: friend@gmail.com
Subject: Важно!
Content-Type: text/plain; charset="UTF-8";

Привет!
```

## 2. Закодируйте письмо

Русский язык не поддерживается в протоколе SMTP, поэтому письмо надо предварительно закодировать в `UTF-8`. Вот как это делается:
```py
letter = """\
From: mymail@gmail.com
To: friend@gmail.com
Subject: Важно!
Content-Type: text/plain; charset="UTF-8";

Привет!"""

letter = letter.encode("UTF-8")

print(letter)
```

Вот что выведет этот код:
```py
b'From: mymail@gmail.com\nTo: friend@gmail.com\nSubject: \xd0\x92\xd0\xb0\xd0\xb6\xd0\xbd\xd0\xbe!\nContent-Type: text/plain; charset="UTF-8";\n\n\xd0\x9f\xd1\x80\xd0\xb8\xd0\xb2\xd0\xb5\xd1\x82!'

```

## 3. Подключитесь к почтовому сервису

С письмом понятно, но как же передать всё это серверу? Чтобы с ним общаться, нужно знать его адрес. Почтовые сайты сами публикуют адреса своих SMTP серверов.

### Адреса для нескольких популярных сервисов:

| Сайт| Адрес сервера |
| :------------- | :-------------:|
| Яндекс.Почта |`smtp.yandex.ru:465`|
| GMail |`smtp.gmail.com:465`|
| Mail.ru |`smtp.mail.ru:465`|


Для примера возьмём Gmail. В первую очередь свяжемся с сервером:
```python
import smtplib

server = smtplib.SMTP_SSL('smtp.gmail.com:465')
```

Затем зайдём в свой почтовый ящик. Для этого передайте методу `.login()` свои логин и пароль:
```python
import smtplib

server = smtplib.SMTP_SSL('smtp.gmail.com:465')
server.login(login, password)
```

## 4. Отправьте письмо

Теперь, когда письмо закодировано, его можно наконец-то отправить. Метод `.sendmail()` ждёт от вас 3 значения: от кого, кому и что передать. Да, вы уже указали это в письме, но придётся указать второй раз:
```python
import smtplib

server = smtplib.SMTP_SSL('smtp.gmail.com:465')
server.login(login, password)
server.sendmail(email_from, email_to, message)
server.quit()
```

Обратите внимание, что в конце мы прощаемся с сервером методом `.quit()`, чтобы он больше не ждал от нас писем. Это правило хорошего тона. Соблюдать его не обязательно, но бездушной машине будет приятно.
