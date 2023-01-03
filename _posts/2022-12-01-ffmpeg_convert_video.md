---
layout: post
title:  ffmpeg
category: Program
---

***Конвертируйте видео файлы в вашей системе Linux с помощью FFmpeg***.

- Откройте Терминал.

- Введите: 

>ffmpeg -i

- Введите имя файла MOV с указанием пути к файлу, например:  

>/home/user/Desktop/sample.mov

- Введите имя выходного файла MP4 с указанием пути к файлу назначения, например:

>/home/user/Desktop/sample.mp4

***Вся команда в этом примере выглядит так***: 

>ffmpeg -i /home/user/Desktop/sample.mov /home/user/Desktop/sample.mp4


Нажмите клавишу «Enter», чтобы начать кодирование видео.

Новый файл **MP4** появится в папке, используемой в пути к целевому файлу, после завершения 
кодирования.


***Еще пример конвертировать видео без каких-либо ограничений***:

> ffmpeg -i video_original.avi video_finale.mp4
