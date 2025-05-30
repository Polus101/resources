# Внутреннее устройство Docker

Прежде, чем начать пользоваться такой внутренне сложной и совершенно новой технологией, стоит разобраться, как Docker работает, из чего состоит и зачем нужны отдельные его компоненты

Мы постараемся максимально легко и просто описать его работу

## Docker Container
Самое простое и для нас самое главное - контейнер! Как говорилось в статье об истории серверов, Docker создает для каждого сервиса (проекта) отдельную мини-виртуальную машину. 

Мини-виртуальная машина максимально урезана - в ней осталось только самое необходимое для запуска сервисов.


**Эти мини-виртуальные машины и есть контейнеры**

<p align="center">
<img src="https://github.com/Polus101/resources/blob/master/Encyclopedia/Docker/img/container.png" style="width:30%"/>
</p>

*Контейнеры так же максимально оптимизированы - например, все контейнеры используют общее ядро и дисковое пространство вместо эмуляции отдельно для каждого контейнера*



## Docker Daemon
Докер `Демон` или `Служба`. Вы его не видите, Вы о нем не думаете, Вы его не замечаете, но именно он обрабатывает все операции связанные с контейнерами. 

Создание, удаление, переименование, запуск, остановка, работа с дисками, сетями, образами и т.д.

Именно он, как невидимый дирижер, управляет всем

<p align="center">
<img src="https://github.com/Polus101/resources/blob/master/Encyclopedia/Docker/img/daemon.png" style="width:60%"/>
</p>

## Docker Client
Тут все просто - клиент - это `докер терминал`, в который вы вводите команды. С помощью него вы даете распоряжения `Службе` докер, сделать что-то. 

Например, создать для Вас новый контейнер)

<p align="center">
<img src="https://github.com/Polus101/resources/blob/master/Encyclopedia/Docker/img/client.png" style="width:50%"/>
</p>


## Docker Desktop
Docker Desktop - то, что Вы больше всего видите перед глазами - это `программа для работы с Docker`.

<p align="center">
<img src="https://github.com/Polus101/resources/blob/master/Encyclopedia/Docker/img/desktop_real.png" style="width:60%"/>
</p>

Помимо того, что это Ваш графический интерфейс, это еще и минималистичная виртуальная машина Linux.

Дело в том, что Docker работает только под Linux, поэтому, если вы работаете на Windows, Docker Desktop приходится создавать виртуалку Linux для своей работы. Именно это и происходит, когда Вы запускаете программу - Вы видите сообщение `Running Docker Engine` - значит, запускаются все компоненты, включая виртуалку Linux

<p align="center">
<img src="https://github.com/Polus101/resources/blob/master/Encyclopedia/Docker/img/desktop.png" style="width:60%"/>
</p>


## Docker Host
Докер хостом называют машину, на которой работает докер. То есть `Ваш компьютер`! Ну или `сервер`, на котором вы запустите свой сайт, бота или любой другой сервис

<p align="center">
<img src="https://github.com/Polus101/resources/blob/master/Encyclopedia/Docker/img/host.png" style="width:60%"/>
</p>


## Docker Image
Docekr Image переводится как докер образ. И это действительно образ! `Образ контейнера`!

Как мы и говорили, контейнер - это мини-виртуальная машина для вашего сервиса (проекта). Любой программе, которую Вы писали, для работы нужны как минимум Python и определенные скачанные библиотеки

Образ - это `описание того, что будет в Вашем контейнере`. По сути - что необходимо Вашей программе для работы. Как `шаблон`, по которому создается контейнер со всем необходимым для программы

*На основе одного образа (шаблона) можно создавать сколько угодно контейнеров, что достаточно удобно*

<p align="center">
<img src="https://github.com/Polus101/resources/blob/master/Encyclopedia/Docker/img/image.png" style="width:80%"/>
</p>

## Docker Repository
Вы уже пользовались Git и GitHub, поэтому знаете, что там репозиторий - это хранилище разных версий вашего проекта. 
Репозиторий докер - то же самое - это `хранилище разных версий образа`

Так же, как и с репозиториями Git, репозитории Docker могут быть локальными (находиться у Вас на компьютере) и удаленными (находиться в облаке)

Самое популярное облако для Git - это GitHub. Ну а для Docker - это `DockerHub`.

<p align="center">
<img src="https://github.com/Polus101/resources/blob/master/Encyclopedia/Docker/img/rep.png"/>
<img src="https://github.com/Polus101/resources/blob/master/Encyclopedia/Docker/img/rep2.png"/>
</p>

**Вот и все! Это финальная схема работы Docker**
Теперь Вы знаете о всех основных компонентах Docker и понимаете, какой из компонентов зачем нужен!
