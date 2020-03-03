# Темы
- Конфиг
- Алиасы
- Атрибуты .gitattributes
- Игнорирование .gitignore
- Удаление
- Ветки


# Конфиг
```
## Содержимое конфига
git config --global --list

## Удаление поля
git config --unset user.name

## Удаление секции
git config --remove-section user
```
Мой конфиг
```
git config --global core.autocrlf true
git config --global core.editor "'c:/program files/sublime text 3/subl.exe' -w"
```


# Алиасы
```
git config --global alias.s 'status'
git config --global alias.c 'config --global'
```
теперь `git s` будет означать `git status`


# Глобальное игнорирование
```
## Создание глобального игнор файла
git config --global core.excludesFile ~/.gitignore
```

Добавляем глобальное игнорирование `.idea` (файл webstorm'а)

`.gitignore`
```
.idea
```


# Удаление
```
## Удаляет файл из индекса, но оставляет в проекте
git rm -r --cached <file>
```


# Ветки
```
## Отмена всех изменений и возврат к начальному состоянию коммита
git checkout -f

## Откат изменений указанных файлов
git checkout HEAD index.html

## Сливает указанную ветку с текущей
git cherry-pick <branch or commit name>

## Берет из указанного коммита только указанный файл
git checkout <commit_name> <file_name>
git checkout e5e6 index.html

## Вернуться на предыдущий чекаут
git checkout -
```


# Коммиты
```
## Удаляет из индекса указанный файл
git reset <file_name>
```


# Log
```
## Выводит информацию о коммитах указанной ветки
git log <branch_name> --oneline

git show <branch_name or commit_name>
```


