---
layout: post
title:  Обновление ядра в Slackware grub
category: Slackware
---

The key thing here is to reject the options to install Lilo or ELilo and drop back to a root prompt after installation has finished but before rebooting.  Then issue the following commands:

***Главное здесь - отклонить варианты установки Lilo или ELilo и вернуться к приглашению root после завершения установки, но перед перезагрузкой. Выдача следующих команд***:

>mount
>
>chroot /mnt /bin/bash
>
>source /etc/profile
>
>grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=grub
>
>grub-mkconfig -o /boot/grub/grub.cfg

***For a non-UEFI system the grub install command is***:

- grub-install --target=x86_64-efi /dev/sda 

*# or whatever your drive is called*

***For virtual box to boot on UEFI you also need to copy grub to a new directory***:

**option creates any intermediate directories**

- mkdir -p /boot/efi/EFI/boot 

*# -p option creates any intermediate directories*

- cp /boot/efi/EFI/grub/grubx64.efi /boot/efi/EFI/boot/bootx64.efi

>Взято: https://www.youtube.com/watch?v=OZeJd5JPQro