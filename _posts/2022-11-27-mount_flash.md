---
layout: post
title:  mount flash
categories: News Linux
---

### Монтирование флешек_mount

#### Команды:

>sudo mkdir /media/flash
> 
>sudo fdisk -l

#### Команда монтирования флешки с **ФС FAT16/32**:

>sudo mount -t vfat /dev/sdXX /media/flash -o uid=1000,utf8

или

>sudo mount /dev/sdXX /media/flash -o uid=1000,utf8

или

>sudo mount -t vfat /dev/sdXX /media/flash -o uid=1000,gid=1000,utf8,dmask=027,fmask=137

#### Команда монтирования флешки с **ФС NTFS**:

>sudo mount -t ntfs-3g /dev/sdXX /media/flash

или

>sudo mount /dev/sdXX /media/flash

#### где:

>/dev/sdXX - раздел, который необходимо примонтировать;
> 
>/media/flash - папка, куда необходимо примонтировать раздел

#### Размонтировать:

>sudo umount /dev/sdXX

где:

>/dev/sdXX - раздел, который необходимо размонтировать

### Монтирование ISO образа в **Linux**

#### Создадим точку монтирования:

>$ sudo mkdir -p /mnt/mount_point

#### Монтирование ISO Файла в Linux

Смонтируем **ISO** файл **/home/user/disk.iso** в точку монтирования **/mnt/mount_point**:

>$ sudo mount -o loop /home/user/disk.iso /mnt/mount_point

 После того, как ISO образ диска будет смонтирован, Вы получите следующее сообщение: ***‘mount: 
 warning: /mnt/mount_point seems to be mounted read-only‘***.

 Можете спокойно его игнорировать, так как в соответствии со стандартом **ISO 9660, ISO образы** 
 всегда монтируются только в режиме **read-only** (только чтение).

Проверяем что *ISO** файл смонтирован:

- Выведите список смонтированных устройств, чтобы убедиться что наш **ISO** образ успешно 
примонтировался:

>$ mount

- Внизу Вы должны увидеть строку на подобии следующей:

>/home/user/disk.iso on /mnt/mount_point type iso9660 (ro)

- Теперь Вы можете перейти в точку монтирования и просмотреть файлы содержащиеся на **ISO** образе 
  диска:

>$ cd /mnt/mount_point
> 
>$ ls -l

#### Размонтирование **ISO** файла в **Linux**

Используйте следующую команду для размонтирования **ISO** образа диска:  ***sudo umount /dev/sdXX***