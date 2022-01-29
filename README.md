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