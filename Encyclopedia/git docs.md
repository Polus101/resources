# Шпаргалка по Git

### Сделать папку репозиторием
Перед работой с гито, надо указать, что папка с проектом будет расцениваться как гит репозиторий:
```
git init
```
На экране получим надписаь `Initialized empty Git repository`:
```
Initialized empty Git repository in C:/Users/PUSH_ka/Desktop/Test/.git/
```


### Проверка статуса
Проверить какие изменения были сделаны в проекте с последнеего коммита
```
git status
```

На экране увидим какие файлы были изменены:
```
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        main.py

nothing added to commit but untracked files present (use "git add" to track)
```

Или так, если изменений не было:
```
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```

### Добавление файлов в коммит
Если файлы были изменены или созданы новые, `git status` вам их покажет. Теперь их надо добавить в новый коммит:
```
git add .
```

`git add` добавит все измененные или созданные файлы в коммит. Если вы хотите добавить в коммит только некоторые изменения, можно это явно указать:
```
git add main.py
```
Команда `git add` ничего не выводит на экран - это нормально. Чтобы проверить, что `add` правильно сработал, можно прописать еще раз статус и убедиться что файлов не осталось

### Коммит
Когда файлы в коммит добавлены, нужно дать ему имя. В имени пишется, что было изменено:
```
git commit -m "Добавил файл main.py"
```
На экране отобразится следующее:
```
[master (root-commit) c269c37] Добавил файл main.py
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 main.py
```
### Отправка изменений на сервер (GitHub)
```
git push
```

### Получение последних изменений с сервера
```
git pull
```

### Скачать репозиторий с сервера на компьютер
```
git clone ссылка_на_репозиторий папка_куда_будет_сохраняться
```
