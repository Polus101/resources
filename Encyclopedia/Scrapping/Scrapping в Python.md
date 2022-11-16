# Scrapping Python

Scrapping - это сбор информации с сайта. Так как сайт состоит из блоков, то и поиск этой информации осуществаяется по блокам.

Если необходимо достатать информацию из `<div class="headline_text">`, то искать мы будем именно его.




## Как с этим работать
Для начала необходимо скачать библиотеку парсера, с помощью которого мы и будем доставать с сайта нужную информацию
```
pip install beautifulsoup4
```

<hr>

После импортируем в код
```python
from bs4 import BeautifulSoup
```

<hr>

Для того, чтобы искать что то в коде сайта, необходимо код сайта сначала получить. Для этого используется обычный `GET` запрос страницу сайта

```python
response = requests.get(url)
response.raise_for_status()
```

<hr>

Затем создается объект парсера. В качестве аргумента передается полученный код сайта и именованный аргумент, в котором указываем, что парсить мы будем html

```python
soup = BeautifulSoup(response.text, features="html.parser")
```

<hr>

Для того чтобы найти какой то элемент, используется метод `find`. Обязательный первый аргумент - тот тэг, который мы ищем
```python
some_headline = soup.find('h2')
```

В переменной `some_headline` будет искомый `h2` - попробуйте вывести ее на экран
**Метод find находит ПЕРВЫЙ элемент, соответствующий условию**. Тоесть в этом примере, он выдаст первый тэг `h2` на странице. 

Если нужно найти НЕ самый первый на странице тэг `h2`, то сначала найдите `div`, в котором он лежит, а уже внутри ищите `h2`

<hr>

Если тэгу присвоен класс - например 
```html
<h2 class="main_headline">
```

То его легко найти, передав необязательный аргумент `class_` в метод `find`
```python
some_headline = soup.find('h2', class_="main_headline")
```

Так он выдаст именно этот `h2`. Если по коду сайта выше нет такого же `h2` с таким же названием класса

Тоже самое для поиска по `id`

<hr>

Пример выше удобен если у тэга указан класс или id, но для поиска по другим артибутам, лучше будет использовать аргумент `attrs`. В него передается словарь

HTML
```html
<div data-foo="value">foo!</div>
```
PYTHON
```python
some_block = soup.find('div', attrs={"data_foo": "value"})
```

<hr>

Если нам нужно найти не один тэг, а все тэги по общему критерию. Например, все заголовки `h2`. В этом случае поможет метод `find_all`. Работает так же как `find`, но ищет не первый элемент, а все элементы. 
```python
some_headline = soup.find_all('h2', class_="headline")
```

<hr>

Если нужно достать только текст из тэга - чтобы не было самих тэгов по краям на выводе:

```python
some_headline = soup.find('h2').text
```

<hr>

Если нужно достать атрибут тэга - например, саму ссылку из тэга `a`, а не текст ссылки:

HTML
```html
<a href="https://www.youtube.com/watch?v=dQw4w9WgXcQ", class="video_magosh">не смотреть ни в коем случае серьезно видео шок</a>
```
PYTHON
```python
link = soup.find('a', class_="video_magosh")["href"]
```

В переменной `link` будет `https://www.youtube.com/watch?v=dQw4w9WgXcQ`

## Пример
**Задача:** Допустим есть сайт, с которого нам необходимо достать заголовок `Легендарный командный шутер компании Valve`.

<img src="https://github.com/Polus101/resources/blob/master/Encyclopedia/Scrapping/img/csgo_headline2_text.png" alt="пример сайта" width="800"/>

**Решение:**

1. Определим в каком блоке находится заголовок

<img src="https://github.com/Polus101/resources/blob/master/Encyclopedia/Scrapping/img/headline2_tag.png" alt="пример сайта" width="300"/>

2. Он находится в тэге `<p>`, который находится внутри `<div class="content_description">`

3. Этого достаточно, так как вряд ли где то выше на сайте есть еще один `div` с таким же названием класса. Если бы, название было более общим, то мы бы искали еще и `div`, в котором лежит наш `<div class="content_description">`

4. Теперь ищем в коде
```python
# ... Выше должен быть запрос на полечение страницы сайта

# Создаем объект парсера
soup = BeautifulSoup(rescponse.text, features="html.parser")
#Ищем div в котором лежит наш p с текстом заголовка
content_description_block = soup.find('div', class_='content_description')
# Внутри нашего div ищем наш p и берем от него только текст
headline_text = content_description_block.find('p').text
```
Таким образом, в переменной headline_text будет тот заголовок, который мы и искали

Можно записать немного короче:
```python
# ... Выше должен быть запрос на полечение страницы сайта

# Создаем объект парсера
soup = BeautifulSoup(rescponse.text, features="html.parser")
#Ищем div, а в нем сразу ищем наш p с текстом заголовка
content_description_block = soup.find('div', class_='content_description').find('p').text
```
Но смотрите, чтобы строчка не была слишком длинной и сложно читаемой)

