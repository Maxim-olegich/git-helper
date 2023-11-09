# Кароче, смотри - GIT
## Навигация
- **cd** - переместит тебя, куда тебе нужно, `cd ~` - вернет домой, а `cd ..` - переместит на папку выше.
- **ls** - покажет, что находится в текущей папке (если указан путь - в указанной папке). С тегом `-a` покажет скрытые файлы и папки.
- **pwd** - отобразит текущую директорую.
## Создание и удаление
- **touch** - создаст файл.
- **mkdir** - папку.
- **rm** - удалит файл. С тегом `-r` удалит и папку (вместе со всей информацией внутри).
- **rmdir** - удалит папку, но только если она пустая.
## Репозиторий
- **git init** - cоздать репозиторий в текущей папке, если я ничего не путаю.
- **git add** - добавить файлы для отслеживания изменений в них, если я ничего не путаю. Тег **--all** добавит все файлы в текущей папке.
- **git status** - посмотреть статус файлов и вообще, нужно ли что-то коммитить.
- **git commit -m 'описание коммита'** - сделать коммит (чтобы это не значило). Не забудь как обычно про тег `-m`.
## Удаленный репозиторий
- **git remote add origin git@СсылочкаНаShhФайл.git** - связать локальный и удаленный репозиторий. Сначала, конечно, нужно создать удаленный репозиторий на гитхабе.
- **git remote -v** - проверить статус удаленного репозитория. В идеале должны быть типа такие строки:
```BASH
origin  git@github.com:Maxim-olegich/git-helper.git (fetch)
origin  git@github.com:Maxim-olegich/git-helper.git (push)
```
- **git push -u origin master** - первый пуш (`push` - синхронизировать локальный и удаленный репозиторий) должен быть такой. Затем просто `git push`.

## Статусы
- **untracked** - файлы, о которых гит знает, но которые он не отслеживает.
- **tracked** - файлы, изменения в которых гит отслеживает.
- **staged** - файлы, добавленные командой `add` в будущий коммит.
- **modified** - файлы, которые были изменены после коммита или после использования команды `add`.

```mermaid
	flowchart TD
		A[untracked] ==> |add| B[staged+tracked]
		B ==> |git commit| C[tracked]
		C ==> |изменения| D[modified]
		D ==> |git add| B
		B --> |изменения| D
		style A fill:#0000CC
		style B fill:#FF8000
		style C fill:#FFF
		style D fill:#FFF
```

## Лог
- **git log** - посмотреть журнал коммитов. В логе можно найти хеш коммита, автора и его электронную почту, дату коммита, а также описание совершенного коммита. 
- **git log --oneline** - сокращенный лог. Отображает сокращенную запись хеша (длинна может быть разная, но уникалность хеша сохраняется) и описание коммита.

## Хеш
- Хеш - основной идентификатор коммита, записанный с помощью алгоритма SHA-1. Хеш коммита можно посмотреть, вызвав команду `git log`

## head всему голова
- файл `HEAD` находится в папке `.git/` и хранит внутри себя ссылку на служебный файл `refs/heads/master` (или `/main`), который содержит хеш последнего коммита.