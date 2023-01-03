---
layout: post
title: Русификация Slackware
category: Slackware
---

 Если вы установили дистрибутив полностью, то вам необходимо поменять всего лишь пару строк 
 чтобы русифицировать **Slackware**. А именно, файлы в директории 

**/etc/rc.d/**

- nano /etc/profile.d/lang.sh

 **Пример содежимого:**
 
*коментируется строчка импортирующая Английский язык и добавляется строчка 
 для импорта Русского языка*

**************************************

>#!/bin/sh
>
>#Set the system locale.  (no, we don’t have a menu for this ;-)
>
>#For a list of locales which are supported by this machine, type:
>
>#locale -a
>
>#en_US is the Slackware default locale:
>
>
>#export LANG=en_US
>
>export LANG=ru_RU.UTF-8

**сохранить:**

- ctrl+o-->Enter-->ctrl+x

**после сохранения сделать исполняемым**

- chmod +x lang.sh

**************************************

- nano /etc/profile.d/lang.csh

Тут всё так же, как и в примере выше.

***********************************

>#!/bin/csh
>
>#Set the system locale.  (no, we don’t have a menu for this ;-)
>
>#For a list of locales which are supported by this machine, type:
>
>#locale -a
>
>#en_US is the Slackware default locale:
>
>#setenv LANG en_US
>
>setenv LANG ru_RU.UTF-8

**сохранить:**

- ctrl+o-->Enter-->ctrl+x

**после сохранения сделать исполняемым**

- chmod +x lang.csh

**********************************
#### Как исправить показ кирилицы в анг.интерфейсе

*В Slackware 15.0 уже все исправлено.Это на всякий случай*.

- nano /etc/rc.d/rc.font

>#!/bin/sh
>
>setfont -v Cyr_a8x16.psfu.gz
>
>for i in 1 2 3 4 5 6;do
>
>echo -ne "\033%G" >/dev/tty$i
>
>done

**сохранить:**

- ctrl+o-->Enter-->ctrl+x

**после сохранения сделать исполняемым**

- chmod +x rc.font
