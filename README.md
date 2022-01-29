 # GIT Documentation
В данном репозитории представлены основные команды работы с git.

## Config
Конфигурация git.

### Просмотр
- Просмотр текущей конфигурации: `git config --list --show-origin`

- Просмотр значения в конфигурации: `git config user.name`

### Изменение
- Имени пользователя:
`git config --global user.name "John Doe"`

- Почты пользователя:
`git config --global user.email johndoe@example.com"`

- Редактора:
`git config --global core.editor vim`
    - В win нужно указывать полный путь к .exe

- Ветка по умолчанию
`git config --global init.defaultBranch main`

## Commit
Перед создание коммитов, нужно проиндексировать хотя бы один файл `git add filename`
### Создание
- Обычный: `git commit -m "initial commit"`
- Быстрая версия, проиндексировать все и сделать commit: `git commit -a -m "fast commit"`

### Изменение
- Если что-то забыли добавить в прошлый коммит: `git commit --amend`
    - Откроет редактор, в котором можно поменять название commit
    - Если прошлый commit уже залит в репозиторий, то придется сделать git pull и пофиксить merge conflicts
- Можно и так: `git commit -a --amend -m "add commit commands"`
