---
layout: post
title:  simple update Slackware
category: Slackware
---

#### Для простого и быстрого обновления Вашего Slackware:

***Рекомендуется отключить обновление компонентов ядра и самого ядра:***

 Поправьте в консоли с помощью:

- \# nano /etc/slackpkg/blacklist 

выключив нужное (удалите решетку перед 
 именем группы пакета **'#'** ).

***Подключить нужное Вам зеркало пакетов:***

(например **mirror.yandex.ru**) 

Поправьте в консоли с помощь:

- \# nano /etc/slackpkg/mirrors

(удалите решетку перед именем зеркала **'#'**)

***Затем наберите в терминале:***

- slackpkg update gpg

- slackpkg update

- slackpkg install-new

- slackpkg upgrade-all

- lilo 

**Вы обновились !**