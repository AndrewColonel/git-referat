
## Реферат по командам Git



### Навигация

- `pwd` (от англ. _**p**rint **w**orking **d**irectory_, «показать рабочую папку») — покажи, в какой я папке;
- `ls` (от англ. _**l**i**s**t directory contents_, «отобразить содержимое директории») — покажи файлы и папки в текущей папке;
- `ls -a` — покажи также скрытые файлы и папки, названия которых начинаются с символа `.`;
- `cd first-project` (от англ. _**c**hange **d**irectory_, «сменить директорию») — перейди в папку `first-project`;
- `cd first-project/html` — перейди в папку `html`, которая находится в папке `first-project`;
- `cd ..` — перейди на уровень выше, в родительскую папку;
- `cd ~` — перейди в домашнюю директорию (`/Users/Username`);
- `cd /` — перейди в корневую директорию.

### Работа с файлами и папками

**Создание**

- `touch index.html` (англ. _touch,_ «коснуться») — создай файл `index.html` в текущей папке;
- `touch index.html style.css script.js` — если нужно создать сразу несколько файлов, можно напечатать их имена в одну строку через пробел;
- `mkdir second-project` (от англ. _**m**a**k**e **dir**ectory_, «создать директорию») — создай папку с именем `second-project` в текущей папке.

**Копирование и перемещение**

- `cp file.txt ~/my-dir` (от англ. _**c**o**p**y_, «копировать») — скопируй файл в другое место;
- `mv file.txt ~/my-dir` (от англ. _**m**o**v**e_, «переместить») — перемести файл или папку в другое место.

**Чтение**

- `cat file.txt` (от англ. _con**cat**enate and print_, «объединить и распечатать») — распечатай содержимое текстового файла `file.txt`.

**Удаление**

- `rm about.html` (от англ. _**r**e**m**ove_, «удалить») — удали файл `about.html`;
- `rmdir images` (от англ. _**r**e**m**ove **dir**ectory_, «удалить директорию») — удали папку `images`;
- `rm -r second-project` (от англ. _**r**e**m**ove,_ «удалить» + _**r**ecursive_, «рекурсивный») — удали папку `second-project` и всё, что она содержит.

### Полезные возможности

- Команды необязательно печатать и выполнять по очереди. Можно указать их списком — разделить двумя амперсандами (`&&`).
- У консоли есть собственная память — буфер с несколькими последними командами. По ним можно перемещаться с помощью клавиш со стрелками вверх (**`↑`**) и вниз (**`↓`**).
- Чтобы не вводить название файла или папки полностью, можно набрать первые символы имени и дважды нажать `Tab`. Если файл или папка есть в текущей директории, командная строка допишет путь сама.  
    Например, вы находитесь в папке `dev`. Начните вводить `cd first` и дважды нажмите `Tab`. Если папка `first-project` есть внутри `dev`, командная строка автоматически подставит её имя. Останется только нажать `Enter`.


### Синхронизация локального и удалённого репозиториев

`git remote add origin https://github.com/YandexPracticum/first-project.git` (от англ. _remote_, «удалённый» + _add,_ «добавить») — привяжи локальный репозиторий к удалённому с URL `https://github.com/YandexPracticum/first-project.git`;

`git remote -v` (от англ. _**v**erbose_, «подробный») — проверь, что репозитории действительно связались;

`git push -u origin main` (от англ. _push_, «толкать») — в первый раз загрузи все коммиты из локального репозитория в удалённый с названием `origin`.

💡 Ваша ветка может называться `master`, а не `main`. Подправьте команду, если это необходимо.

`git push` (от англ. _push_, «толкать») — загрузи коммиты в удалённый репозиторий после того, как он был привязан с помощью флага `-u`.

### Копирование чужих репозиториев

**Клонирование**

`git clone git@github.com:TheGreatOwner/the-great-project.git` (от англ. _clone_, «клон», «копия») — склонируй репозиторий с URL `the-great-project.git` из аккаунта `TheGreatOwner` на мой локальный компьютер.

**«Форк»**

«Форк» — операция, которая не связана с Git напрямую и выполняется через графический интерфейс GitHub (кнопка Fork в правом верхнем углу страницы репозитория). «Форк» создаёт независимую копию репозитория со всеми файлами, коммитами и ветками в аккаунте GitHub. Такая копия будет полностью независима. Внесённые изменения не будут синхронизированы с исходным репозиторием.

💡 Комбинацию «форк» + `clone` часто используют для внесения изменений в публичные репозитории. В этом случае «форк» становится подготовительным этапом перед клонированием чужого репозитория на локальный компьютер.

Если репозиторий приватный или это репозиторий вашей компании, при работе с ним достаточно `clone`.

### SSH-ключи

- Протокол SSH обеспечивает безопасный обмен данными в сети. С его помощью можно получать данные с удалённого компьютера или отправлять их на него. Трафик шифруется, поэтому протокол безопасен.
- SSH-ключ состоит из двух частей — публичной и приватной. Приватный ключ хранится только на вашем компьютере и не должен передаваться кому-либо ещё. Он используется для расшифровки данных. Публичный ключ доступен всем и используется для шифрования данных. Они могут быть расшифрованы парным приватным ключом.
- Файл с расширением `.pub` содержит публичный ключ, им можно делиться с веб-сайтами или коллегами. Файл без расширения `.pub` — приватный.
- Прежде чем генерировать новую пару ключей, следует убедиться, что они отсутствуют на вашем компьютере. Проверить это можно командой `ls -la .ssh/` в домашней директории. Если ключи отсутствуют, создать их можно командой `ssh-keygen` в директории `~/.ssh`. После генерации ключ нужно привязать к GitHub.


#### YandexGPT

экспериментальный ответ нейросети

- Шпаргалка по командам Git содержит все основные команды и их вариации.
- Команды навигации: pwd, ls, ls -a, cd, cd ~, cd /
- Работа с файлами и папками: touch, mkdir, cp, mv, cat, rm, rmdir
- Полезные возможности: использование двух амперсандов (&&) для разделения команд, перемещение по буферу с помощью клавиш со стрелками, использование Tab для сокращения имен файлов и папок
- Терминал - мощный инструмент с бесконечным количеством команд и параметров, рекомендуется использовать поисковики и шпаргалки для запоминания.
 Git - инструмент командной работы, позволяющий создавать удаленные репозитории и связывать их с локальными.
- Основные команды: git remote add origin, git remote -v, git push -u origin main.
- Копирование чужих репозиториев: git clone, "fork" (операция через графический интерфейс GitHub).
- SSH-ключи: протокол SSH обеспечивает безопасный обмен данными, состоит из публичной и приватной частей.
- Файл с расширением .pub - публичный ключ, файл без расширения .pub - приватный ключ.
- Перед генерацией новой пары ключей следует убедиться, что они отсутствуют на компьютере.
- После генерации ключ нужно привязать к GitHub.


### Дополнительное задание для любознательных

Если у вас осталось время, попробуйте использовать формат описания схем [Mermaid](https://github.blog/2022-02-14-include-diagrams-markdown-files-mermaid/). Принцип такой: вы описываете схему в специальном текстовом формате, а GitHub превращает описание в полноценную схему с блоками и стрелками. Отлично подойдёт для схемы изменения статусов!

Подсказка: как сделать mermaid-схему

Чтобы получить `mermaid`-схему в `README.md`, нужно добавить блок кода типа `mermaid`.

Скопировать код

MARKDOWN

````
HEAD -- это голова.
Коммит -- это всему голова.
Статусы файлов:
<тут пустая строка!>

```mermaid
%% описание схемы
```
<и тут пустая строка!> 
````

Разберём те правила синтаксиса, которые понадобятся вам для выполнения задания:

- Блоки кода в маркдауне начинаются и заканчиваются тремя символами ` ``` `. После первых трёх ` ``` ` можно указать, какой именно код будет внутри блока. Например: ` ```mermaid ` , ` ```bash ` , ` ```python ` , ` ```javascript ` и так далее. Если ничего не указать, GitHub будет считать весь код простым текстом.

💡 Перед блоком и после него нужны пустые строки, иначе GitHub может не понять, что это блок кода.

- Два символа `%%` обозначают в `mermaid` строку-комментарий.
- Чтобы сделать схему, нужно указать формат: `graph LR`. **Graph** — это простейший тип схем; для шпаргалки его будет достаточно.
- Чтобы добавить элементы и связи (стрелки), используют строки вида `A --> B`. Такая строка создаст квадратные блоки `А` и `B` и соединит их стрелкой.  
    Дополнительно можно указывать текст на стрелке. Например, так: `A -- "text" --> B`.

Ниже вы найдёте заготовку для схемы статусов файлов.

Скопировать код

````
```mermaid
graph LR;
  untracked -- "git add" --> staged;
  staged    -- "???"     --> tracked/comitted;

%% стрелка без текста для примера: 
  A --> B;
``` 
````

Попробуйте описать схему самостоятельно и посмотреть, что получится!