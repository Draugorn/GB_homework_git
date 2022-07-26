# Немного о ГитХабе
## Краткое вступление

![Bask in the glory of the GIT](https://cdn.freebiesupply.com/logos/large/2x/git-icon-logo-png-transparent.png)

Сегодня я бы хотел поговорить о системе контроля версий, а именно о Git (читается как ГИТ, а не ДЖИТ, что может показаться из грамматики английского языка).    

Да-да, продвинутые пользователи возможно слышали еще и Mercurial, SVN и плеяде других вариантов. Но будем откровенны (*по крайней мере исходя из того, что я увидел в интернете*): их время уже ушло, и тратить ваше драгоценное время на них не собираюсь.  

Чтобы вы понимали **важность знания гита** в наше время, скажу так: без знания/понимания этого вам делать в программировании нечего. Но прелесть в том, что для постоянной работы не нужно держать в голове все команды и возможности. Нужно знать набор команд, которые помогут понимать всё, что происходит.

## Основы GIT  

Git — это распределенная система контроля версий нашего кода. Зачем она нам? Для распределенных команд нужна какая-то система управления работы. Нужна, чтобы отслеживать изменения, которые происходят со временем. 

То есть шаг за шагом мы видим, какие файлы изменились и как. Особенно это важно, когда анализируешь, что было проделано в рамках одной задачи: это дает возможность возвращаться назад.

Представим себе ситуацию: был работающий код, всё в нем было хорошо, но мы решили что-то улучшить, там подправить, сям подправить. Все ничего, но такое улучшение поломало половину функционала, сделало невозможным работу. И что дальше? Без Гита нужно было бы часами сидеть и вспоминать, как же все было изначально. А так мы просто откатываемся на коммит назад — и все. 

Или что делать, если есть два разработчика, которые делают одновременно свои изменения в коде? Без Гита это выглядит так: они скопировали код из оригинала, сделали что нужно. Наступает момент, и оба хотят добавить свои изменения в главную папку. И что делать в этой ситуации?.. Я даже не берусь оценить время, чтоб проделать эту работу.

**Таких проблем не будет вовсе, если пользоваться Гитом.** 

## Установка Git

Установить Git на компьютер очень просто:  
* **Linux** — нужно просто открыть терминал и установить приложение при помощи пакетного менеджера вашего дистрибутива. Для Ubuntu команда будет выглядеть следующим образом:

> sudo apt-get install git  

* **Windows** - Всё просто, устанавливаем отсюда [Волшебная гиперссылка](https://git-scm.com/book/ru/v2/%D0%92%D0%B2%D0%B5%D0%B4%D0%B5%D0%BD%D0%B8%D0%B5-%D0%A3%D1%81%D1%82%D0%B0%D0%BD%D0%BE%D0%B2%D0%BA%D0%B0-Git)  
* **OS X** - OS X — проще всего воспользоваться homebrew. После его установки запустите в терминале:
> brew install git

Если вы новичок, клиент с графическим интерфейсом(например GitHub Desktop и Sourcetree) будет полезен, но, тем не менее, знать команды очень важно.

## Настройка

Итак, мы установили git, теперь нужно добавить немного настроек. Есть довольно много опций, с которыми можно играть, но мы настроим самые важные: наше имя пользователя и адрес электронной почты. Откройте терминал и запустите команды:  

> git config --global user.name "My Name"  
> git config --global user.email myEmail@example.com  

Теперь каждое наше действие будет отмечено именем и почтой. Таким образом, пользователи всегда будут в курсе, кто отвечает за какие изменения — это вносит порядок.
Git хранит весь пакет конфигураций в файле .gitconfig, находящемся в вашем локальном каталоге. Чтобы сделать эти настройки глобальными, то есть применимыми ко всем проектам, необходимо добавить флаг –global. Если вы этого не сделаете, они будут распространяться только на текущий репозиторий.
Для того, чтобы посмотреть все настройки системы, используйте команду:

> git config --list  

Если вы не до конца настроили систему для работы, в начале своего пути - не беда. Git всегда подскажет разработчику, если тот запутался, например:

1. Команда git --help - выводит общую документацию по git  
2. Если введем git log --help - он предоставит нам документацию по какой-то определенной команде (в данном случае это - log)
3. Если вы вдруг сделали опечатку - система подскажет вам нужную команду
4. После выполнения любой команды - отчитается о том, что вы натворили
5. Также Гит прогнозирует дальнейшие варианты развития событий и всегда направит разработчика, не знающего, куда двигаться дальше

Тут стоит отметить, что подсказывать система будет на английском, но не волнуйтесь, со временем вы изучите несложный алгоритм ее работы и будете разговаривать с ней на одном языке.  

## Создание нового репозитория  

Как мы отметили ранее, git хранит свои файлы и историю прямо в папке проекта. Чтобы создать новый репозиторий, нам нужно открыть терминал, зайти в папку нашего проекта и выполнить команду init. Это включит приложение в этой конкретной папке и создаст скрытую директорию .git, где будет храниться история репозитория и настройки.
Создайте на рабочем столе папку под названием git_exercise. Для этого в окне терминала введите:

> mkdir Desktop/git_exercise/  
> cd Desktop/git_exercise/  
> git init

Командная строка должна вернуть что-то вроде:

> Initialized empty Git repository in /home/user/Desktop/git_exercise/.git/  

Это значит, что наш репозиторий был успешно создан, но пока что пуст. Теперь создайте текстовый файл под названием hello.txt и сохраните его в директории git_exercise.

## Определение состояния

status — это еще одна важнейшая команда, которая показывает информацию о текущем состоянии репозитория: актуальна ли информация на нём, нет ли чего-то нового, что поменялось, и так далее. Запуск git status на нашем свежесозданном репозитории должен выдать:

> $ git status  
> On branch master  
> Initial commit  
> Untracked files:  
> (use "git add ..." to include in what will be committed)  
> hello.txt  

Сообщение говорит о том, что файл hello.txt неотслеживаемый. Это значит, что файл новый и система еще не знает, нужно ли следить за изменениями в файле или его можно просто игнорировать. Для того, чтобы начать отслеживать новый файл, нужно его специальным образом объявить.

В git есть концепция области подготовленных файлов. Можно представить ее как холст, на который наносят изменения, которые нужны в коммите. Сперва он пустой, но затем мы добавляем на него файлы (или части файлов, или даже одиночные строчки) командой add и, наконец, коммитим все нужное в репозиторий (создаем слепок нужного нам состояния) командой commit.
В нашем случае у нас только один файл, так что добавим его:  

> git add hello.txt

Если нам нужно добавить все, что находится в директории, мы можем использовать:  

> git add -A

Проверим статус снова, на этот раз мы должны получить другой ответ:  

> $ git status  
> On branch master  
> Initial commit  
> Changes to be committed:  
> (use "git rm --cached ..." to unstage)  
> new file: hello.txt  

Файл готов к коммиту. Сообщение о состоянии также говорит нам о том, какие изменения относительно файла были проведены в области подготовки — в данном случае это новый файл, но файлы могут быть модифицированы или удалены.  

Но, это только самое начало, а файл уже и так затянулся!
Поэтому, на этом моменте, я откланяюсь, подсунув вместо себя фото ***прекрасного*** кота! 

![picturename.cat](http://fotorelax.ru/wp-content/uploads/2020/12/20201227-Photos-of-cats-12_1-min.jpg)  

Пожалуй, на этом стоит остановиться, но прежде чем мы разойдемся, я хотел бы кратко показать возможности языка markdown, на котором написана эта инструкция.

## MarkDown - кратко

В данном документе будут описаны основные возможности языка в максимально упрощенном для понимания формате.  
Начать, думаю, стоит с **определения** языка:  
> Markdown (произносится маркда́ун) — облегчённый язык разметки, созданный с целью обозначения форматирования в простом тексте, с максимальным сохранением его читаемости человеком, и пригодный для машинного преобразования в языки для продвинутых публикаций (HTML, Rich Text и других).  

И, конечно, приправить определение историей языка честно ~~скопированной~~ позаимствованной из Википедии:  
> Первоначально создан в 2004 году Джоном Грубером и Аароном Шварцем. Многие идеи языка были позаимствованы из существующих соглашений по разметке текста в электронных письмах. Реализации языка Markdown преобразуют текст в формате Markdown в валидный, правильно построенный XHTML и заменяют левые угловые скобки («<») и амперсанды («&») на соответствующие коды сущностей. Первой реализацией Markdown стала написанная Грубером реализация на Perl, однако спустя некоторое время появилось множество реализаций от сторонних разработчиков. Реализация на Perl распространяется по лицензии типа BSD. Реализации Markdown на различных языках программирования включены (или доступны в качестве плагина) во многие системы управления содержимым.  

## - Основные возможности языка  
Но, достаточно историй и определений! Перейдём к изучению того инструментария, который заложен в язык.  
Во-первых, Markdown даёт нам не одну, не две, и даже не три ступеньки заголовков (это те самые, которые разделяют блоки нашего маленького гайда). Технически, их тут больше чем пальцев у меня на руке, так что считать не будем.  
Вызвать их – проще простого: просто добавляем в начале строки символ «#» и вуаля – заголовок первого уровня. Два #? – получите заголовок второго уровня. Три? Ну, я думаю, вы поняли.  
Что интересно, заголовки можно вызывать заголовки можно и иначе – складируя под линией текста-заголовка символы «=» для первого уровня или «-» для уровня второго *(но это не так удобно)*.  
Далее! Если вы уже начали пробовать набирать свой первый файл, то возможно, у вас возжник вопрос: *«как этот колдун сделал переносы строк в своём тексте??»*  
«Ха!» - отвечу я. ~~ - Всего 100 золотых монет и я поделюсь этой великой мудростью с вами!~~ Просто поставьте **два пробела в конце строки**. Да, я тоже не сразу постиг эту древнюю истину.  
А для разделения текста на параграфы, просто добавьте между ними **пустую строку**.  

А теперь перейдём к толстому и итальянскому тексту. Ой. К тексту **bold** и *italic*, конечно. И, что характерно, несмотря на огромные различия в их внешнем виде, у них гораздо больше общего, чем может показаться! Вся их разница – в количестве астерисков (или подчеркиваний) вокруг слова: «**» или «__» дадут нам **bold**. А если оставить «*» или «_» в одиночестве – получится *italic*.  
Но если и этого мало, то можно совместить их воедино, создав монстра - ***bold italic***. Для этого количество волшебных элементов увеличивается до трёх – «***» или «___».

На этом, пожалуй, откланяюсь, пожелав всем присутствующим хорошего обучения!  
А команде GB - прекрасных учеников.  
Ну и ***огромную*** благодарность. :)

Ну а теперь, важное и интересное: **Подключение к удаленному репозиторию**!

Чтобы загрузить что-нибудь в удаленный репозиторий, сначала нужно к нему подключиться. Регистрация и установка может занять время, но все подобные сервисы предоставляют хорошую документацию.  
Чтобы связать наш локальный репозиторий с репозиторием на GitHub, выполним следующую команду в терминале.  

> $ git remote add origin https://github.com/username/repository

Проект может иметь несколько удаленных репозиториев одновременно. Чтобы их различать, мы дадим им разные имена. Обычно главный репозиторий называется origin.

Сейчас самое время переслать наш локальный коммит на сервер. Этот процесс происходит каждый раз, когда мы хотим обновить данные в удаленном репозитории.
Команда, предназначенная для этого - push. Она принимает два параметра: имя удаленного репозитория (мы назвали наш origin) и ветку, в которую необходимо внести изменения (master — это ветка по умолчанию для всех репозиториев).

> $ git push origin master

Эта команда немного похожа на git fetch, с той лишь разницей, что при помощи fetch мы импортируем коммиты в локальную ветку, а при применив push, мы экспортируем их из локальной в удаленную. Если вам необходимо настроить удаленную ветку используйте git remote. Однако пушить надо осторожно, ведь рассматриваемая команда перезаписывает безвозвратно все изменения. В большинстве случаев, ее используют, чтобы опубликовать выгружаемые локальные изменения в центральный репозиторий. А еще ее применяют для того, чтобы поделиться, внесенными в локальный репозиторий, нововведениями, с коллегами или другими удаленными участниками разработки проекта. Подытожив сказанное, можно назвать git push - командой выгрузки, а git pull и git fetch - командами загрузки или скачивания. После того как вы успешно запушили измененные данные, их необходимо внедрить или интегрировать, при помощи команды слияния git merge.  
В зависимости от сервиса, который вы используете, вам может потребоваться аутентифицироваться, чтобы изменения отправились. Если все сделано правильно, то когда вы посмотрите в удаленный репозиторий при помощи браузера, вы увидите файл hello.txt    

Всё, на этом точно откланяюсь. :) 