# Aliases
Для создания более сокращенных алиасов, нужно их записывать в .bash_aliases.

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
```

Теперь команда в терминале `g` будет соответсвовать 'git'
