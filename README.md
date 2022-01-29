 # GIT Documentation
В данном репозитории представлены основные команды работы с git.

## Config
Конфигурация git.

#### Просмотр
- Просмотр текущей конфигурации: `git config --list --show-origin`

- Просмотр значения в конфигурации: `git config user.name`

#### Изменение
- Имени пользователя:
`git config --global user.name "John Doe"`

- Почты пользователя:
`git config --global user.email johndoe@example.com"`

- Редактора:
`git config --global core.editor vim`
    - В win нужно указывать полный путь к .exe

- Ветка по умолчанию
`git config --global init.defaultBranch main`

- Создание alias:
    - `git config --global alias.last 'log -1 HEAD'`
    - `git last`

## Remote
Управление репозиториями

- Вывести репозитории: `git remote` / `git remote -v`
- Добавить репозиторий: `git remote add nameRepo url`
- Вывести подробную информацию: `git remote show nameRepo`
- Переименовать репозиторий: `git remote rename nameRepo newNameRepo`
- Удалить репозиторий: `git remote rm nameRepo`

## Log
Вывод информации о commits.
- Показать коммиты: `git log`
    - Все коммиты: `git log --all`
    - Удобный вывод: `git log --oneline --graph --all`
- Показать изменения в коммитах: `git log -p`
    - Кратко: `git log --stat`
- Ограничить вывод: `git log -3`
- Посмотреть commits ветки: `git log branchName`
- Без слияний: `git log --no-merges`

#### Форматирование вывода
- `git log --pretty=oneline` - еще shor, full, fuller
- `git log --pretty=format:"%h - %an, %ar : %s"`
- Покажет ветки и слияния: `git log --graph`
    - Удобный вывод: `git log --oneline --graph`

#### Фильтрация
- По времени
    - За последнии 2 недели: `git log --since=2.weeks`
    - До этого числа `git log --since="2021-10-01"`
    - Раньше 2 недель: `git log --until=2.weeks`
- Найти commits, где была изменена строка: `git log -S db_fetch_method()`

## Commit
Перед создание коммитов, нужно проиндексировать хотя бы один файл `git add filename`

#### Создание
- Обычный: `git commit -m "initial commit"`
- Быстрая версия, проиндексировать все и сделать commit: `git commit -a -m "fast commit"`

#### Изменение
- Если что-то забыли добавить в прошлый коммит: `git commit --amend`
    - Откроет редактор, в котором можно поменять название commit
    - Если прошлый commit уже залит в репозиторий, то придется сделать git pull и пофиксить merge conflicts
- Можно и так: `git commit -a --amend -m "add commit commands"`

## Pull, Push, Fetch
fetch - получения данных из удалённых проектов (origin)
- `git fetch origin`

push - отправка данных в репозиторий
- `git push origin main`

pull - получение данных и сливание
- `git pull origin main`

## Reset, Restore
- Отменить индексирование (git add):
    - `git reset HEAD fileName`
    - `git restore --staged fileName`
- Востановить файл(ы) из прошлого commit:
    - `git checkout someFile.txt`
    - `git restore someFile.txt`

## Tags
Пометки на commits, к примеру для обозначения версий.

Git использует два основных типа тегов: легковесные и аннотированные.
Легковесный - просто указатель на определённый коммит.
Аннотированные - хранятся в базе данных Git как полноценные объекты.

#### Создание
- Создание легковесного: `git tag v1.1`
- Создание аннотированного: `git tag -a v1.1 -m "my version 1.1"`
- Пометка старых коммитов: `git tab -a v1.0 9ac421`

#### Просмотр
- Просмотр: `git tag`
- Фильтр: `git tag -l "v1.5.*"`
- Просмотр тега: `git show v1.1`

#### Отправка
- Отправка тега на сервер: `git push origin v1.1`
- Отправка всех: `git push origin --tags`
- Отправка только аннотированных: `git push origin --follow-tags`

#### Удаление
- Удаляет локально: `git tag -d v1.1`
- Удаляет на сервере:
    - `git push origin :refs/tags/v1.1`
    - `git push origin --delete v1.1`

#### Переход на тег
- `git checkout v1.1`
- Если нужно внести изменения - исправить ошибку в одной из старых версий - следует создать ветку: `git checkout -b version2 v1.1`

## Ветвление

- Создать ветку: `git branch branchName`
- Переключиться на ветку: `git checkout branchName`
- Создать и переключиться: `git checkout -b branchName`
- Можно использовать `git switch`
    - Создать и переключиться: `git switch -c branchName`
    - Переключиться: `git switch branchName`
    - Вернуться к предыдушей извлечённой ветки: `git switch -`