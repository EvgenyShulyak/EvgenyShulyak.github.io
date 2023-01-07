---
layout: post
title:  slackware afte install
category: Slackware
---


#### Slackware(настройка сразу после установки)

- 1.При первой загрузке вводим имя пользователя(доступен только root)

- 2.Пароль,который задали при установке

- 3.И наконец вводим ***startx > Enter***.Все загружается система.

- 4.После загрузки добавляем пользователя и пароль пользователя: 

***adduser > Enter > name user***

- 5.Если нужно добавляем sudo:

***nano /etc/sudoers***

В указанном файле отыскивается строка

 ***# WHEEL_USERS ALL=(ALL) ALL***
 
 С коей и снимается символ комментария. При желании совсем облегчить себе жизнь та же процедура 
 проделывается со строкой

 ***# WHEEL_USERS ALL=(ALL) ALL NOPASSWD: ALL***
 
- 6.Перезагрузка:

**Вводим имя пользователя,пароль и startx**

- 7.После загрузки системы добовляем репозиторий для обновлений:

***nano /etc/slackpkg/mirrors***

Раскомментируем ОДНО зеркало:

в ***nano /etc/slackpkg/mirrors***

(убираем слеш **#** в нужной строке "зеркале")

Сохраняем:**Ctrl+O > Enter > Ctrl+X**

Далее обновлямся под рутом:

 - slackpkg update
 
 - slackpkg update gpg
 
 - slackpkg upgrade-all(снимаем галочки в пунктах,где первым идет слово kernel - их 6 пункта.
 Иначе могут быть ошибки.)
 
 - lilo
 
#### Русификация

***KDE5 Plasma можно русифицировать в настройках(графический интерфейс)***

 Если вы установили дистрибутив полностью, то вам необходимо поменять всего лишь пару строк. А 
 именно, файлы в директории ***/etc/rc.d/***

Изменение локали делают внутри файла ***/etc/profile.d/lang.sh*** и ***/etc/profile.d/lang.csh***

 Пример содежимого.
 
Коментируется строчка импортирующая Английский язык и добавляется строчка 
 для импорта Русского языка

**************************************

>**#!**/bin/sh
> 
>Set the system locale.  (no, we don’t have a menu for this ;-)
> 
>For a list of locales which are supported by this machine, type:
> 
 >locale -a
> 
>n_US is the Slackware default locale:

Меняем содержимое файла:

***nano /etc/profile.d/lang.sh***

>(#)export LANG=en_US
> 
>export LANG=ru_RU.UTF-8

**************************************

Далее, меняем содержимое файла:

***nano /etc/profile.d/lang.csh***

Тут всё так же, как и в примере выше.

***********************************

>**#!**/bin/csh
> 
>Set the system locale.  (no, we don’t have a menu for this ;-)
> 
>For a list of locales which are supported by this machine, type:
>
>locale -a
>
>en_US is the Slackware default locale:
> 
>(#)setenv LANG en_US
> 
>setenv LANG ru_RU.UTF-8

**********************************
#### Как исправить показ кирилицы в анг.интерфейсе

***nano /etc/rc.d/rc.font***

>**#!**/bin/sh
> 
>setfont -v Cyr_a8x16.psfu.gz
> 
>for i in 1 2 3 4 5 6;do
> 
>echo -ne "\033%G" >/dev/tty$i
> 
>done
>
>chmod +x rc.font

**********************************

Далее необходимо перезагрузить иксы (***CTRL+alt+BACKSPACE***) или компьютер (по желанию).