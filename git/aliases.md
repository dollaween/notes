# Aliases
Для создания более сокращенных алиасов, нужно их записывать в `.bash_aliases`.

Убеждаемся в существовании следующих файлов по пути:

`/Users/<name>/.bashrc`
```
if [ -f ~/.bash_aliases ]; then
. ~/.bash_aliases
fi
```

`/Users/<name>/.bash_aliases`
```
alias g="git"
alias gs="git status"

# add commit push одной командой
function gacp() {
    git add .
    git commit -m "$1"
    git push
}
```

Теперь команда в терминале `g` будет соответсвовать `git`
