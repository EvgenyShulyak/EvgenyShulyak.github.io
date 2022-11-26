---
layout: post
title:  archivers in terminal
categories: News Linux
---

#### Архив ZIP

- архивирование файла:

zip архив.zip файл

- архивирование директории:

zip -r архив.zip директория/

- повышение уровня сжатия:

zip -0 архив.zip файл

zip -9 архив.zip файл

- защита архива паролем
не рекомендуемая опция, показывает пароль:

zip -P пароль архив.zip файл

- безопасная опция, пароль запрашивается и скрывается при вводе:

zip -e архив.zip файл

- разархивирование:

unzip архив.zip

- детальный вывод информации при распаковке:

unzip -v архив.zip

- получение списка содержимого архива:

unzip -l архив.zip

- проверка архива на повреждение:

atoolunzip -t архив.zip

#### Архив TAR

- архивирование файла или директории без сжатия:

tar -cf архив.tar файл

- дополнительный ключ "v", для подробного вывода процесса архивации:

tar -cvf архив.tar директория/

- архивирование с использованием сжатия gzip:

tar -zcvf архив.tar.gz файл

tar -zcvf архив.tar.gz директория/

- архивирование с использованием сжатия bzip2:

tar -jcvf архив.tar.bz2 файл

tar -jcvf архив.tar.bz2 директория/

- проверка архива gzip без распаковки:

tar -zvtf архив.tar.gz

- проверка архива bzip2 без распаковки:

tar -jvtf архив.tar.bz2

- распаковка архива gzip:

tar -zxvf архив.tar.gz

- распаковка архива bzip2 с указанием конечной папки для файлов:

tar -jxvf архив.tar.bz2 директория/

#### Команды Tar:

    x — извлечь файлы из архива;
	
    v — подробный вывод информации на экран;
	
    f — Обязательная опция. Если не указать, Tar будет пытаться использовать магнитную ленту вместо файла;
	
    z — обработать архив сжатый gzip’ом;
	
    j — обработать архив сжатый bzip’ом.

***копирование файлов в Linux с помощью tar***

Linux интересен тем, что позволяет выполнять одно и то же действие различными путями. Копирование в Linux тоже может быть выполнено не только с помощью cp. При переносе системных файлов в другой каталог, резервном копировании системных файлов и т.д. важно чтобы сохранились атрибуты, значения владельцев файлов и символические ссылки как они есть без какой-либо модификации.

Утилита cp тоже может справиться с такой задачей? если указать опцию -p, но можно использовать утилиту архивации tar. Мы не будем создавать никаких файлов архивов, а построим туннель. Первая часть команды пакует файл и отправляет на стандартный вывод, а другая сразу же распаковывает в нужную папку:

***tar cf - /var | ( cd /mnt/var && tar xvf - )***

Здесь мы полностью копируем содержимое папки /var в папку /mnt/var. Так вы можете копировать папку Linux, причём абсолютно любую или даже целую операционную систему.

Архив 7z

#### устанавливаем:

***sudo apt-get install p7zip p7zip-full***

- архивируем:

7z a arch.7z file01.foo file02.foo

- распаковка:

7z x arch.7z

7z x arch.7z -o/куда_извлекать

- просмотр архива:

7z l arch.7z

7z l -slt arch.7z

#### atool

- установка:

***sudo apt-get install atool***

- распаковка:

aunpack foobar.tar.gz

- архивирование:

apack myarchive.zip file1 file2

#### in ranger_команды_архивации:

map ex extract

map ec compress

#### Архив LZMA

- установка:

***sudo aptitude install lzma***

- Упаковать файл. Внимание! архивируется сам файл,
т.е. из файла получится архив! самого файла после упаковки не будет!:

lzma -z filename

- Распаковка:

lzma -d filename.lzma

#### Архив RAR

- упаковка:

rar -a архив.rar директория/
	
- распаковка:

unrar архив.rar

 ***Примечание: Стоит отметить, что Unrar может отсутствовать по умолчанию в некоторых 
 Linux-дистрибутивах.***