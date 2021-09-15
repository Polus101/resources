JLinker

Что делает JLinker
Linker вставляет текст из нескольких файлов в один

Для чего?
Например, еесли вы хотите разделить ваш большой JS файл на несколько маленьких. Это может быть полехно, если у вас большой проект, который необходимо разделить на несколько файлов. Вы можете положить классы в отдельные файлы.

How to install Linker to your project?
Проосто скачайте архив с github и разархивируйте его в своем JS проекте

Например:

├─ index.html/      
├─ style.css/
├─ Game/
│  ├─ GameLevels/
│  ├─ Objects/
├─ ZEngine/     
│  ├─ EngObject/         
│  ├─ Tools/        
│  ├─ Init.js   
│  ├─ Scene.js          
└─ JLinker/
   ├─ linker.py/         
   ├─ default_linked_dirs.py/         
   └─ README.md/


Как использовать Linker?
По стандарту Linker соединяет файлы в директориях 'engine', 'graphics', 'game' и их поддиректориях. Если вы хотите их изменить, вам необходимо отредактировать linkedDirs в linker.py
Чтобы запустсить Linker вам необходимо установить Python 3 и написать в консоли команду py/python3 path to your linker.py. Вы можете использовать как абсолютный, так и относительный путь

py GCup/JLinker/linker.py.
