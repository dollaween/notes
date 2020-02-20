# Темы
- Конфиг
- Алиасы
- Атрибуты .gitattributes
- Игнорирование .gitignore
- Удаление


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
