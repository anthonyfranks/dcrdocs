# Запросы Pull Request и сотрудничество с Decred 

---

Весь код для Decred хранится на GitHub. В этом документе представлена основная информация о том, как мы осуществляем сотрудничество по коду и некоторая базовая информация о том, как можно поучаствовать. Он частично основывается на похожем документе в [btcsuite](https://github.com/btcsuite).

---

## Первоначальная подготовка 

Первый правильный шаг [Code Contribution Guidelines documentation](https://github.com/decred/dcrd/blob/master/docs/code_contribution_guidelines.md) для получения четкого представления об основных принципах, используемых
проектом.  Этот документ в первую очередь ориентирован на кодовую базу Go (Go codebase), но тем не менее, это неплохо для начала.

Следующие примеры будут распределены на два раздела: один для проектов Go (dcrd, dcrwallet, gominer и т. Д.), и другой для проектов, которые не используют Go (decrediton, paymetheus, dcrdocs и т.д.). Во всех случаях обязательно проверяйте README.md в каждом проекте, если Вам нужна помощь в настройке конкретного проекта.

---

## Общая модель 

Данным образом мы стараемся сделать процес содействия простым, сохраняя при этом высокий уровень качества кода и чистую историю. Члены команды Decred должны соблюдать те же процедуры, что и внешние участники.

Наша модель для работы с кодом в общих чертах выглядит следующим образом. Если Вам что-то не понятно, не беспокойтесь, все будет объяснено более подробно в следующих разделах.

1. Найдите проблему, с которой хотите работать. Если никто ее не описывает, откройте новую с тем, что собираетесь делать.
1. Внесите изменения кода в ветку.
1. Вставьте эти изменения в свое собственное ответвление GitHub.
1. 1.Когда Ваш код готов к пересмотру или Вы просто нужны данные других разработчиков откройте "Подать запрос" (Pull Request (PR) на основном repo с веб-страницы GitHub.
1. Добавьте комментарий к PR, указав, какую проблему Вы исправляете. Поместите текст Closes # (завершается) или Fixes # (исправляется), а затем номер проблемы одной строкой. Это позволит GitHub автоматически увязать PR с проблемой и закрыть проблему, когда PR закрыт.
1. Вы можете запросить конкретного проверяющего с веб-страницы GitHub, или же Вы можете попросить проверить кого-то на irc / slack.
1. ВСЕ коды должен быть просмотрены, и получено как минимум одно одобрение, прежде чем смогут пойти в работу. Только члены команды могут дать официальное одобрение, но комментарии других пользователей поощряются.
1. Если требуется внести изменения, внесите их и передайте (commit) их в свою локальную ветку.
1. Вставьте (push) эти изменения в ту ветку, которую Вы обрабатывали. Так они будут отображаться в PR, и проверяющий может затем сравнить с предыдущей версией.
1. Once your code is approved, it can be merged into master.  To keep history clean, we only allow non-fast-forward merges (that means we want a linear history).  Most PRs also must be squashed to a single commit (although if there is reason to have it as multiple commits that can be considered on a case by case basis).
1. Если Ваш PR подается одноразово(или же может быть сжат GitHub автоматически), и мастер принял его, проверяющий объединит ваш PR. Если Ваша ветка слишком отстала, Вас могут попросить переместить (rebase) Ваш commit. Как только это будет сделано и вставлено, проверяющий объединит Вашу подачу.

---

## Go 

Для проектов, использующих Go, Вы можете следовать этой процедуре. В качестве примера будет использоваться Dcrd. Предполагается, что у Вас уже установлен go1.6 или более новый, и работает `$GOPATH`.

### Единовременная установка
- Сделайте развилку dcrd на GitHub
- Запустите следующие команды, чтобы получить dcrd, все, с ним связанное,и установите его:

```bash
$ mkdir -p $GOPATH/src/github.com/decred/
$ git clone https://github.com/decred/dcrd $GOPATH/src/github.com/decred/dcrd
$ go get github.com/Masterminds/glide
$ cd $GOPATH/src/github.com/decred/dcrd
$ glide install
$ go install $(glide nv)
```

- Добавьте git remote для своей развилки:

```bash
$ git remote add <yourname> https://github.com/<yourname>/dcrd.git
```

## Другие проекты 

Для проектов, написанных не в Go, первоначальная установка будет зависеть от проекта. В качестве примера я буду использовать dcrdocs, но основные шаги одинаковы для всех проектов. Конкретные установки можно увидеть в проекте README.md (например, как установить mkdocs для работы на dcrdocs или electron для decrediton).

### Единовременная установка 
- Сделайте развилку dcrdocs на GitHub.
- Запустите следующие команды, чтобы получить dcrd, все, с ним связанное,и установите его:

```bash
$ mkdir -p code/decred
$ cd code/decred
$ git clone https://github.com/decred/dcrdocs
$ cd dcrdocs
```

- Добавьте git remote в свою развилку:

```bash
$ git remote add <yourname> https://github.com/<yourname>/dcrdocs.git
```

## Создание запроса (Pull Request) на добавление новой функции 
- Найдите или создайте проблему в repo GitHub (оригинале, не Вашей развилке) для функции, над которой Вы хотите работать.
- Наладьте (Checkout) ветку новой функции, чтобы размещать изменения, которые Вы будете производить:

```bash
$ git checkout -b <feature_branch>
```
- Внесите изменения, необходимые для функции, и подайте (commit) их
- Вставьте (push) ветку новой функции в свою развилку:

```bash
$ git push <yourname> <feature_branch>
```
- В браузере перейдите на страницу https://github.com/decred/dcrd
- Создайте запрос PR на GitHub. Вы можете запросить проверяющего с веб-страницы GitHub, или Вы можете попросить кого-нибудь в irc / slack.

## Перемещение одного из Ваших существующих запросов PR. 

Иногда Вас попросят переместить (rebase) и сжать (squash) запрос PR для самой последней master branch.

- Убедитесь, что master branch обновлена:

```bash
$ git checkout master
$ git pull
```
- Наладьте существующую ветку функции и переместите ее с интерактивным флагом:

```bash
$ git checkout <feature_branch>
$ git rebase -i master
```
- Follow the directions presented to specify 's' meaning squash for the additional commits (the first commit must remain 'p' or 'pick').
- Напишите одиночное коммит-сообщение в редакторе, который Вы настроили для охвата всех включенных коммитов).
- Сохраните и закройте редактор, git должен создать одиночный коммит с написанным Вами сообщением, и всеми добавленными Вами коммитами. Вы можете проверить коммит командой ```git show```.
- Вставьте ветку в свою развилку:

```bash
$ git push -f <yourname> <feature_branch>
```

## Другие аспекты 

Есть еще несколько вещей, которые следует учитывать при выполнении запроса PR. В случае с кодом Go уже имеется значительное тестовое покрытие. Если Вы добавляете код, Вы должны также добавить и тесты. Если Вы что-то исправляете, Вам нужно убедиться, что Вы не нарушаете уже существующих тестов. Для кода Go в каждом repo есть скрипт ```goclean.sh``` для запуска тестов и любых статических проверок, которые у нас есть. Ни один из кодов не будет принят без прохождения всех тестов. В случае кода node.js (decrediton) весь код должен пройти eslint. Вы можете проверить это с помощью команды ```npm run lint```.

Наконец, у каждого repo есть ЛИЦЕНЗИЯ. Ваш новый код должен находиться под той же ЛИЦЕНЗИЕЙ, что и существующий код, и ему присвоены авторские права 'The Decred Developers'. В большинстве случаев это очень либеральная лицензия ISC, но некоторые repo отличаются. На всякий случай проверьте repo.

Если у вас есть какие-либо вопросы по участию, пожалуйста, спрашивайте на irc / slack или GitHub. Члены команды Decred (и, возможно, члены сообщества тоже) будут рады Вам помочь.
