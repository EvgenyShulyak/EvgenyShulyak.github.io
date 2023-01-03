---
layout: post
title:  youtube-dl
category: Program
---


**youtube-dl** есть в каталогах пакетов некоторых дистрибутивов Linux: ***sudo apt-get install 
youtube-dl, sudo yum install youtube-dl, sudo pacman -S youtube-dl*** 

 Помимо того, чтобы получить список всех доступных форматов видео, которое вы хотите загрузить с 
 утилитой **youtube-dl**, необходимо использовать вариант ***--list-formats***, как показано ниже 
 (пример):

>youtube-dl --list-formats https://www.youtube.com/watch?v=ySzrJ4GRF7s

 Я для примера выбрал формат под **номером 1**, с расширением **mp4**.Этот формат нужно добавить в 
 команду после **youtube-dl**, как показано ниже в команде (пример):

>https://www.youtube.com/watch?v=ySzrJ4GRF7s

Другие возможности утилиты youtube-dl, можно посмотреть в терминале, выполнив команду:

>youtube-dl --help

Команда для скачивания:

>youtube-dl -Aciw адрес с ютуба

Для скачивания всего плейлиста, достаточно ввести ссылку на плейлист:

>$ youtube-dl -Acitf 18  http://www.youtube.com/playlist?list=ссылка-на-плейлист

#### -Acitf — это параметры, вот их расшифровка:

    -A — автонумерация.
    -с — в случае обрыва соединения, продолжит с момента обрыва, после повторного ввода команды в том же каталоге.
    -i — игнорирование ошибок.
    -t — назвать файл, так же как имя записи.
    -f 18 — выбор формата и качества (см. выше).

Если нужен только аудио трек, тогда введем аргумент **-х**:

>$ youtube-dl -x http://www.ссылка-на-видео

Чтобы скачать нужное видео с **YouTube** достаточно выполнить команду в **Терминале**:

>youtube-dl ссылка_на_видео

 По флагу -F будут показаны все доступные форматы. Если ввести флаг **-f** с числовым кодом 
 формата, 
 он будет выкачан. Комбинация **-f bestaudio** выкачает аудио в лучшем формате.

Для выбора нужного видео формата и качества, используем параметр **-F**:

Должны увидеть примерно такой вывод:

>youtube-dl -F https://www.youtube.com/watch?v=Pi4uQl_0T2w

- [youtube] Setting language
- [youtube] Pi4uQl_0T2w: Downloading webpage
- [youtube] Pi4uQl_0T2w: Downloading video info webpage
- [youtube] Pi4uQl_0T2w: Extracting video information
- [info] Available formats for Pi4uQl_0T2w:

#### format code extension resolution note

- 171 webm audio only DASH webm audio , audio@ 48k (worst)
- 140 m4a audio only DASH audio , audio@128k
- 160 mp4 192p DASH video
- 242 webm 240p DASH webm
- 133 mp4 240p DASH video
- 243 webm 360p DASH webm
- 134 mp4 360p DASH video
- 244 webm 480p DASH webm
- 135 mp4 480p DASH video
- 247 webm 720p DASH webm
- 136 mp4 720p DASH video
- 248 webm 1080p DASH webm
- 137 mp4 1080p DASH video
- 17 3gp 176×144
- 36 3gp 320×240
- 5 flv 400×240
- 43 webm 640×360
- 18 mp4 640×360
- 22 mp4 1280×720 (best)

Напротив формата имеется цифра, например ***22 : mp4 1280×720 (best)***, именно ее нужно 
использовать для выбора качества, после параметра -f:

>youtube-dl -f 22 ссылка_на_видео

Чтобы скачать весь плейлист, нужно ввести ссылку на плейлист в команду:

>youtube-dl -f 22 https://www.youtube.com/channel/UCQBEHg0j6baNS1Lya-L4BJw

Чтобы скачать видео в определенный каталог нужно зайти в эту директорию при помощи команды cd и выполнить команду для скачивания. Например:

>cd /home/user/save_video

>youtube-dl -citw https://www.youtube.com/channel/UC9FSFwSIfqQkePaU

Основные параметры youtube-dl:

- -A — автонумерация.

- -с — если произойдет обрыв соединения, то утилита продолжит скачивание с момента обрыва, после 
 повторного ввода команды в том же каталоге.

- -i — игнорировать ошибки.

- -t — присвоить имя файлу такое же как и имя записи.

- —audio-format — указать формат сохраняемого аудио файла (mp3, aac, wav, m4a, vorbis)

- —audio-quality — качество аудио файла. 0 (лучше), 9 (хуже) для VBR или конкретный битрейт, 
 например 128K (по умолчанию 5)

- -f 22 — выбор формата и качества.

- -w — не перезаписывать файл.

- -s — симуляция скачивания. Файл не не скачивается и не сохраняется на жесткий диск.

- -x — используем, если нужно скачать только звук.
-o — параметр указывает каталог для сохранения. По умолчанию программа скачивает в Домашнюю папку.

- -a — возможность скачать группу файлов из текстового файла. Адреса нужных видео файлов 
 вписываете в текстовый файл в таком порядке:

>https://www.youtube.com/watch?v=JIrm0dHbCDU
> 
>https://www.youtube.com/watch?v=diT3FvDHMyo
> 
>https://www.youtube.com/watch?v=Fy7FzXLin7o

и сохраняем его в Домашнем каталоге присвоим имя, например, ***video.txt***. Чтобы скачать весь 
этот список выполним команду:

>youtube-dl -a video.txt

Чтобы скачать видео конкретного пользователя, в нашем случае BlackSilverUfa, выполним следующую команду:

>youtube-dl -citw ytuser:BlackSilverUfa

Чтобы сохранить видео в нужный каталог используем ключ -P:

>wget -P /home/user/save https://www.youtube.com/playlist?list=PLG4Fqn_lntSq

Чтобы скачать в папку с названием Пользователя и оригинальным именем файлов, выполним:

>youtube-dl -ciw ytuser:UCBB7mGxCAfQYqLgqNukEbtg -o '%(uploader)s/%(title)s'

Скачать и пронумеровать файлы с оригинальным названием в Домашнюю папку:

>youtube-dl -ciw ytuser:UCBB7mGxCAfQYqLgqNukEbtg -o '%(autonumber)s_%(title)s.%(ext)s' 
> --autonumber-size 2

Скачать и пронумеровать файлы с оригинальным названием в каталог с именем Пользователя:

>youtube-dl -ciw ytuser:UCBB7mGxCAfQYqLgqNukEbtg -o '%(uploader)s/%(autonumber)s_%(title)s.%(ext)
> s' --autonumber-size 2

Скачать только звук:

>youtube-dl -x ytuser:UCBB7mGxCAfQYqLgqNukEbtg

Скачать только звук в формате mp3 и в лучшем качестве VBR в каталог с именем Пользователя с нумерацией файлов:

>youtube-dl -ciw ytuser:UCBB7mGxCAfQYqLgqNukEbtg -x --audio-format mp3 --audio-quality 0 -o '%
> (uploader)s/%(autonumber)s_%(title)s.%(ext)s' --autonumber-size 2

Чтобы узнать все ключи и параметры утилиты выполните команду:

>man youtube-dl

