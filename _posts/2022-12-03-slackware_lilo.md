---
layout: post
title:  Обновление ядра в Slackware lilo
category: Slackware
---

 Обновление ядра в **Slackware** проходит автоматически при выполнении команды **slackpkg 
 upgrade-all** 
  и ядро по умолчанию даже не добавлено в blacklist пакетного менеджера. Что может доставить 
 изрядно проблем после обновления.

 Дело в том, что ядро корректно устанавливается и даже обновляются символические ссылки в папке 
 **/boot** для **lilo**. Но при этом не собирается новое initrd.

 **initrd** это образ файловой системы с некоторым набором программ и модулями ядра, например, 
 таким как **ext4** для доступа к файловой системе. initrd запускается самой первой, монтирует корень и 
долее запускает основное ядро и всю систему.

 Так вот, со старым **initrd** не получится подмонтировать корневой раздел диска и вы получите 
 ошибку при запуске **Slackware**
 
 
***Чтобы такого не произошло, достаточно выполнить одну команду для сборки нового initrd. Нужно 
 перейти в папку /boot и выполнить команду. В моем случае она будет следующей***:

>mkinitrd -c -k 5.13.4 -r /dev/sda2 -f ext4 -m ext4
> 
>OK: /lib/modules/5.13.4/kernel/fs/jbd2/jbd2.ko added.
> 
>OK: /lib/modules/5.13.4/kernel/fs/mbcache.ko added.
>
>OK: /lib/modules/5.13.4/kernel/fs/ext4/ext4.ko added.
56144 blocks
>
>boot/initrd.gz created.

***Be sure to run lilo again if you use it***.

 С учетом того, что у меня **Slackware** установлен на **/dev/sda2** и используется в качестве 
 файловой 
  системы **ext4**. У вас параметры могут отличатся. Данная команда соберет новый **initrd** и 
 можно 
 будет смело перезагрузится.

 **Так же, чтобы не писать эту команду можно создать специальный конфигурационный файл 
 /etc/mkinitrd.conf следующего содержания**:

>KERNEL_VERSION=$(readlink /boot/vmlinuz-generic | cut -d- -f3)
MODULE_LIST="ext4"
ROOTDEV="/dev/sda1"
ROOTFS="ext4"

**После этого достаточно будет выполнять команду со следующими параметрами**:

>mkinitrd -c -F

Но есть ещё один способ от самого Патрика.

***Это скрипт***:

>/usr/share/mkinitrd/mkinitrd_command_generator.sh

 ***Он позволяет в автоматическом режиме сгенерировать команду для запуска сборки initrd. У него 
 есть помощь, а также можно запросить текущие настройки выполнив***:

>/usr/share/mkinitrd/mkinitrd_command_generator.sh -c

- SOURCE_TREE="/boot/initrd-tree"
- CLEAR_TREE="1"
- OUTPUT_IMAGE="/boot/initrd.gz"
- KERNEL_VERSION="5.13.4"
- KEYMAP="us"
- MODULE_LIST="xhci-pci:ohci-pci:ehci-pci:xhci-hcd:uhci-hcd:ehci-hcd:hid:usbhid:i2c-hid
  :hid_generic:hid-asus:hid-cherry:hid-logitech:hid-logitech-dj:hid-logitech-hidpp:hid-lenovo:hid-microsoft:hid_multitouch:jbd2:mbcache:crc32c_intel:crc32c_generic:ext4"LUKSDEV=""
- ROOTDEV="/dev/sda1"
- ROOTFS="ext4"
- RESUMEDEV=""
- RAID=""
- LVM=""
- UDEV="1"
- WAIT="1"

***Если выполнить скрипт с ключом -i***:

>/usr/share/mkinitrd/mkinitrd_command_generator.sh -i

 Будет вызван интерактивный режим пошаговыми с запросами параметров. После выполнения будет 
 выдана команда для выполнения.
 
***Например, такая***:

>mkinitrd -c -k 5.13.4 -f ext4 -r /dev/sda1 -m 
> xhci-pci:ohci-pci:ehci-pci:xhci-hcd:uhci-hcd:ehci-hcd:hid:usbhid:i2c-hid:hid_generic:hid-asus:hid-cherry:hid-logitech:hid-logitech-dj:hid-logitech-hidpp:hid-lenovo:hid-microsoft:hid_multitouch:jbd2:mbcache:crc32c_intel:crc32c_generic:ext4 -u -o /boot/initrd.gz

***Либо новое ядро можно указать непосредственно через ключь***:

>/usr/share/mkinitrd/mkinitrd_command_generator.sh -k 5.13.4
>
>lilo

***Взято: 27.07.2021 https://slackware-alive.ru/slackware-kernel-upgrade/***