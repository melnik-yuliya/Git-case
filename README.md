

# Система контроля версий, 
или VCS (SCM), — программа, позволяющая контролировать изменения в проекте.

**Git** — один из примеров системы контроля версий: он позволяет хранить, изменять и анализировать историю проекта.

**Git** — незаменимый в команде инструмент, ведь он помогает объединять результаты работы нескольких человек.


## Основные функции системы контроля версий:

- хранит историю изменений в виде отдельных ревизий;

- позволяет манипулировать историей: например, менять порядок ревизий, полностью удалять версии, возвращаться назад в истории;

- помогает анализировать изменения: например, кто и когда вносит изменения, кто чаще всего вносит изменения в определённый файл и так далее.


**Git** — это программа, которая в том числе может работать из командной строки. Любой графический интерфейс для Git всего лишь преобразует клики пользователя в вызовы программы.
Введите pwd в командную строку и нажмите клавишу Enter для выполнения команды. Командная строка выведет путь к папке, в которой вы сейчас находитесь.
Обычно здесь хранится такая информация, как загрузки, медиа, скриншоты и так далее. Когда вы открываете командную строку, вы оказываетесь именно в домашней директории.

Если вы пользователь Windows, то Git у вас уже есть. Вы установили его в составе пакета Git for Windows вместе с командной строкой.

## Навигация
- pwd (от англ. print working directory, «показать рабочую папку») — покажи, в какой я папке;
- ls (от англ. list directory contents, «отобразить содержимое директории») — покажи файлы и папки в текущей папке;
- ls -a — покажи также скрытые файлы и папки, названия которых начинаются с символа .;
- cd first-project (от англ. change directory, «сменить директорию») — перейди в папку first-project;
- cd first-project/html — перейди в папку html, которая находится в папке first-project;
- cd .. — перейди на уровень выше, в родительскую папку;
- cd ~ — перейди в домашнюю директорию (/Users/Username);
- cd / — перейди в корневую директорию.

## Работа с файлами и папками
### Создание
touch index.html (англ. touch, «коснуться») — создай файл index.html в текущей папке;
touch index.html style.css script.js — если нужно создать сразу несколько файлов, можно напечатать их имена в одну строку через пробел;
mkdir second-project (от англ. make directory, «создать директорию») — создай папку с именем second-project в текущей папке.
### Копирование и перемещение
```
cp file.txt ~/my-dir 
mv file.txt ~/my-dir
```
### Чтение
```
cat file.txt
```
### Удаление
```
rm about.html 
rmdir images 
rm -r second-project
``` 
### Полезные возможности
Команды необязательно печатать и выполнять по очереди. Можно указать их списком — разделить двумя амперсандами (&&).
У консоли есть собственная память — буфер с несколькими последними командами. По ним можно перемещаться с помощью клавиш со стрелками вверх (↑) и вниз (↓).
Чтобы не вводить название файла или папки полностью, можно набрать первые символы имени и дважды нажать Tab. Если файл или папка есть в текущей директории, командная строка допишет путь сама.
Например, вы находитесь в папке dev. Начните вводить cd first и дважды нажмите Tab. Если папка first-project есть внутри dev, командная строка автоматически подставит её имя. Останется только нажать Enter.


## Что такое SSH
Когда компьютеры обмениваются данными в сети, они следуют сетевым протоколам (англ. network protocols) — правилам обмена данными между компьютерами.
Один из наиболее распространённых сетевых протоколов — SSH (от англ. Secure Shell Protocol). Он обеспечивает безопасный обмен данными в сети. С помощью этого протокола можно получать данные с удалённого компьютера или отправлять их на него. Трафик шифруется, поэтому протокол безопасен.
SSH использует пару ключей для обеспечения безопасности — публичный и приватный: 
**Приватный ключ** (англ. private key) хранится только на вашем компьютере и не должен передаваться кому-либо ещё. Он используется для расшифровки данных.
**Публичный ключ** (англ. public key) доступен всем и используется для шифрования данных. Они могут быть расшифрованы парным приватным ключом.
Только вы можете расшифровать данные с помощью приватного ключа, но любой владелец публичного ключа может их для вас зашифровать. Эти два ключа связаны и образуют SSH-пару. В будущем вы наверняка будете использовать их для взаимодействия с GitHub и другими удалёнными серверами.
## Проверка наличия SSH-ключа
Прежде чем генерировать SSH-ключи, убедитесь, что у вас их ещё нет. По умолчанию директория с SSH-ключами находится в домашней директории пользователя. Перейдите в неё.
```
$ cd ~ 
``` 
Обычно SSH-ключи находятся в директории .ssh/. Проверить наличие этой директории и файлов в ней можно с помощью следующей команды.
```
$ ls -la .ssh/
``` 
Если папка пустая или её нет, всё в порядке. 


## Инструкция по генерации SSH-ключа
Для генерации SSH-пары можно использовать программу ssh-keygen. Откройте терминал и введите следующую команду.
```
$ ssh-keygen -t ed25519 -C "электронная почта, к которой привязан ваш аккаунт на GitHub" 
```

Используйте электронную почту, к которой привязан ваш GitHub-аккаунт.
	
	
## Инструкция по связыванию SSH-ключа и GitHub-аккаунта
1. После выполнения команды ssh-keygen из предыдущего урока в директории ~/.ssh будет создано два файла — id_ed25519 и id_ed25519.pub:
id_ed25519 — приватный ключ (файл без .pub в конце). Ни в коем случае не копируйте его и не делитесь им.
id_ed25519.pub — публичный ключ (на это указывает расширение .pub).
2. Скопируйте содержимое файла с публичным ключом в буфер обменаб для этого выведите содержимое файла с помощью cat ~/.ssh/id_ed25519.pub и скопируйте вывод в буфер обмена из консоли.
3. Перейдите на GitHub и выберите пункт Settings (англ. «настройки») в меню аккаунта.
4. В меню слева нажмите на пункт SSH and GPG keys.
5. В открывшейся вкладке выберите New SSH key (англ. «новый SSH-ключ»).
6. В поле Title (англ. «заголовок») напишите название ключа. Например, Personal key (англ. «личный ключ»).
7. В поле Key type (англ. «тип ключа») должно быть Authentication Key (англ. «ключ аутентификации»).
8. В поле Key скопируйте ваш ключ из буфера обмена.
9. Нажмите на кнопку Add SSH key (англ. «добавить SSH-ключ»).
10.Проверьте правильность ключа с помощью следующей команды.
```
$ ssh -T git@github.com 
```

Вы прошли весь «цикл коммита»: подготовили файлы с помощью _git add_, 
закоммитили их с комментарием командой git commit -m. 
Осталось загрузить содержимое локального репозитория на GitHub. 
За это отвечает команда git push (от англ. push — «толкать»).
В первый раз эту команду нужно вызвать с флагом -u и параметрами origin (имя удалённого репозитория) и main или master (название текущей ветки). 
Флаг -u свяжет локальную ветку с одноимённой удалённой. Как вы связывали локальный и удалённый репозитории в предыдущем уроке, так же и здесь нужно дополнительно связать ветки.
```
$ git push -u origin main 
``` 
Если команда приведёт к ошибке, попробуйте заменить main на master. 
						  
Коммиты хранятся в ветках. Начальная ветка создаётся автоматически и называется main или master.
За отправку изменений на удалённый репозиторий отвечает команда _git push_.
Интерфейс GitHub позволяет удобно просмотреть все коммиты в репозитории, а также изменения в этих коммитах.

Чтобы другие пользователи, а также потенциальные клиенты или работодатели могли понять, что представляет собой проект, его нужно описать. Такое описание принято указывать в файле **README.md** 

## Уникальный идентификатор

Git преобразует информацию о коммитах с помощью алгоритма SHA-1 и для каждого из них рассчитывает уникальный идентификатор — **хеш**.

Хеш — основной идентификатор коммита и позволяет узнать его автора, дату и содержимое закоммиченных файлов.

Все хеши, а также таблицу соответствий хеш → информация о коммите Git хранит в папке .git.

```
 git log --oneline
```
 
Получить сокращённый лог можно с помощью команды git log с флагом --oneline (англ. «одной строкой»). В терминале появятся только первые несколько символов хеша каждого коммита и их комментарии.

**Обратите внимание:** если выход из просмотра логов не произошёл автоматически, нажмите клавишу Q (от англ. Quit — «выйти») в английской раскладке клавиатуры.

## Статусы файлов
```mermaid
flowchart TD
A[файл untracked]-- git add --> B{файл staged/tracked};
B -- файл изменён --> C[файл modified/staged/tracked];
B -- git commit --> D[файл tracked];
C -- git add --> B;
D -- файл изменён --> F[файл modified/tracked];
F -- git add --> B;
```

Статусом untracked помечается файл, о существовании которого Git знает, но не следит за изменениями в нём. Этот статус — противоположность tracked, в который попадают все файлы, отслеживаемые Git.

Файл переходит в статус staged после выполнения git add.

Статус modified означает, что файл был изменён.

Большинство файлов в проектах «шагает» по следующему циклу: «изменён» → «добавлен в список на коммит» → «закоммичен» → «изменён» → и так далее.

Команда git status всегда подскажет, что происходит с файлом: например, он добавлен в список «на коммит» или ещё вообще не отслеживается, или изменён.

git status показывает явно следующие состояния файлов: untracked, staged и modified.

git status подсказывает, какие команды можно выполнить, чтобы поменять состояние файла.

## Правила оформления коммита

* сообщение коммита легко читается;

* оно информативное;

* все сообщения оформлены в одном стиле.