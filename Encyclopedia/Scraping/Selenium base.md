# Автоматизация браузера с помощью Selenium

Селениум позволяет взаимодействовать с элементами страницы так, будто это делает реальный пользователь: писать что то в строки, удалять написанный текст, кликать на элементы, перетаскивать их, сворачивать окно, разворачивать, изменять размер и т.д.

Работать мы будем с библиотекой selenium. Предварительно ее необходимо скачать
```
pip install selenium
```


## Содержание 
- [Базовое использование](#base_usage)
- [Открытие страниц](#open_page)
- [Поиск элементов](#find)
- [Поиск элемента внутри другого](#find_in)
- [Получение информации из найденного элемента](#get_info)
- [Основные действия с элементами](#elem_work)
- [Пользовательские данные](#user_data)
  


<a name="base_usage"><h2>Базовое использование</h2></a>

Как мы помним, в переменную можно сохранить что угодно
Первое, что мы делаем - создаем переменную, в которой будет лежать наш браузер! А именно вебдрайвер нашего браузер
```python
driver = webdriver.Chrome()
```
Для того, чтобы эта строчка сработала, необходимо импортировать объект webdriver из библиотеки selenium:
```python
from selenium import webdriver
```
В данном случае, селениум будет использовать стандартный вебдрайвер браузера хром, который у вас установлен на ПК. Конечно, если у вас установлен браузер хром (или браузер, созданый на основе хром) на ПК. И если селениум сможет самостоятельно найти к нему путь

Этого уже достаточно, чтобы все "работало". Попробуйте запустить данный код.
Вы увидите, что у вас запустился браузер и тут же закрылся. 
Программа выполнена! `driver = webdriver.Chrome()` запускает драйвер и кладет его в переменную. Именно это и сделала ваша программа. Так как больше строк кода в ней нет, она завершила работу

Чтобы вы успели попользоваться браузером, можете поставить задержку после открытия драйвера time.sleep(10)

Как видно, теперь мы можем полноценно пользоваться новым открывшимся браузером. Правда, всего 10 секунд

<a name="open_page"><h2>Открытие страниц</h2></a>

Заставить наш браузер автоматически открыть какую то страницу легко:
```python
driver.get(url)
```
Например:
```python
driver.get("https://www.google.ru")
```

<a name="find"><h2>Поиск элементов</h2></a>
Чтобы взаимодействовать с элементом, элемент сначала нужно найти

Заранее необходимо импортировать объект `By` - он позволяет выбрать способ поиска элемента
```python
from selenium.webdriver.common.by import By
```

Метода для поиска элементов два:
- `driver.find_element` - ищет только первый элемент (аналог метода `find` в `bs4`)
- `driver.find_elements` - ищет все элементы, подходящие по условию (аналог метода `find_all` в `bs4`)

Поиск элементов осуществляется несколькими путями:
- По id элемента или имени класса (к этому мы привыкли еще из bs4)
```python
element = driver.find_element(By.ID, 'element_id')
```
```python
element = driver.find_element(By.CLASS_NAME, 'element_class')
```
Заметьте, что в bs4 можно было сразу указать, какой тэг мы ищем. Тоесть мы могли искать одновременно по тэгу и классу `soup.find('div', class_="element_class")`
В selenium такой возможности, к сожалению, нет
- По имени (name) элемента. Такие элементы встречаются редко, но все же. Например: `<input name="user_FIO" type="text" value="user name" />`
```python
element = driver.find_element(By.NAME, 'user_FIO')
```
- По тэгу. Например, если нам нужно найти все тэги `h1`
```python
element = driver.find_element(By.TAG_NAME, 'h1')
```
- По тексту. Например, мы ищем элемент, в котором написано `Купить`
```python
element = driver.find_element(By.LINK_TEXT, 'Купить')
```
Так же можно применить поиск по куску текста. Например, если у вас есть кнопка, на которой написано `Купить *что-то*` и вы не знаете, что именно будет после слова Купить
```python
element = driver.find_element(By.PARTIAL_LINK_TEXT, 'Купить')
```
- Но наиболее часто используемый и удобный в селениум способ - поиск по XPATH
```python
element = driver.find_element(By.XPATH, '//*[@id="app"]/div[2]/p')
```

**XPath** - это путь к элементу внутри HTML кода. Вы знаете, что каждый элемент лежит внутри какого-то другого. А он в свою очередь в каком-то другом и т.д. XPath - это путь - указание как добраться до нужного нам элемента

Например, у нас есть HTML код:
```HTML
<!DOCTYPE html>
<html lang="ru">
  <body>
    <h1>Это заголовок</h1>
    <p>А это какой то текст</p>
    <p>А это еще какой то текст</p>
  </body>
</html>
```

В данном случае первый тэг `<p>` находится в `body`. А `body` в свою очередь находится в `html`. 

Тогда путь до тэга `p` будет: `html/body/p[0]`
Для тэгов `html` и `body` мы не указывали квадратные скобки, так как они существуют только в одном экземляре, а вот тэга `p` у нас два. Поэтому в пути мы указали, что нам необходим тэг с индексом 0. Как когда мы работаем со списками в Python

**На самом деле, вам не нужно особо вникать, как именно составляются пути в XPath - там еще очень много правил. Объяснение было дано для общего понимания**

Чтобы узнать XPath тэга, наведитесь в консоли разработчика и нажмите правой кнопкой мыши. После выберите `copy` -> `copy XPath`

<a name="find_in"><h3>Поиск элемента внутри другого</h3></a>

В bs4 мы могли сначала найти какой-то `div` (например), а затем внутри него найти что то еще. В selenium так же есть эта возможность:
```python
some_div = driver.find_element(By.XPATH, '//*[@id="app"]/div[2]/div[3]/div)
another_h2_inside = some_div.find_element(By.TAG_NAME, 'h2')
```
Здесь мы вначале нашли какой то див, а затем нашли в нем какой то h2. Тоесть методы поиска `find_element` и `find_elements` можно применять и к самим найденным элементам

<a name="get_info"><h2>Получение информации из найденного элемента</h2></a>
После того, как мы нашли элемент, мы можем узнать информацию о нем:

- Мы можем получить название самого тэга элемента
```python
element.tag_name
```
- Можем получить любой атрибут этого тэга
```python
element.get_dom_attribute('class')
```
или
```python
element.get_attribute('class')
```
- Или можем получить полностью весь тэг 
Вместо артибута `class` укажте атрибут `innerHTML` или `outerHTML`

Обратите внимание: если заданного атрибута у тэга нет, метод вернет `None`
- Можем получить текст элемента
```python
element.text
```
<a name="elem_work"><h2>Основные действия с элементами</h2></a>
Как говорилось ранее, библиотека позволяет полностью автоматизировать работу с браузером так, будто им пользуется реальный человек. То-есть с помощью кода можно не только получить тэги и их данные со страницы,
но и "нажимать" на элементы, перетаскивать, печатать, удалять и т.д. С помощью кода можно сделать все, что вы можете сделать в браузере руками

**Вы можете работать с элементом (нажать на него, напечатать в него что-то т.д.) только после того, как найдете его!**

Здесь перечислены основный функции, которые понадобятся вам для парсинга и автоматизации работы с сайтом. Если понадобятся любые другие специфические функции, они довольно просто находятся в интернете

#### Нажать на элемент
```python
buy_button = driver.find_element(By.XPATH, '//*[@id="app"]/div[2]/button[0]')
  
buy_button.click()
```


#### Напечатать текст
```python
email_field = driver.find_element(By.XPATH, '//*[@id="app"]/div[1]/textarea')
  
email_field.send_keys("emailid@lambdatest.com")
```

#### Стереть текст
```python
email_field = driver.find_element(By.XPATH, '//*[@id="app"]/div[1]/textarea')
  
email_field.clear()
```

<a name="user_data"><h2>Пользовательские данные</h2></a>

Попробуйте открыть в своем личном обычном браузере страницу [apteka.ru](https://apteka.ru/search/?q=%D0%BF%D0%B0%D1%80%D0%B0%D1%86%D0%B5%D1%82%D0%B0%D0%BC%D0%BE%D0%BB)

В первый раз страница попросит выбрать город

Во второй раз даже после перезапуска браузера страница уже не будет запрашивать город. Сайт запомнил город, который вы выбрали

Однако, в селениуме этого не происходит. Каждый запуск селениума как первый. Он не сохраняет данные сессии и куков - тоесть пользовательские данные. Это стоит учитывать, когда вы пишите программу. Хотя, в селениум есть возможность сохранять эти данные - подробнее об этом будет далее
