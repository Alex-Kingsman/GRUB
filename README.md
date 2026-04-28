ДЗ Загрузка системы

Включить отображение меню Grub
nano /etc/default/grub

#GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10

Обновляем конфигурацию загрузчика
sudo update-grub
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.17.0-22-generic
Found initrd image: /boot/initrd.img-6.17.0-22-generic
Found memtest86+x64 image: /boot/memtest86+x64.bin
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
Adding boot menu entry for UEFI Firmware Settings ...
done

Перезагружаем
sudo shutdown -r now

Попасть в систему без пароля несколькими способами

#1
Способ 1. init=/bin/bash
ok

#2
Recovery mode
ok

#3 Установить систему с LVM, после чего переименовать VG

vgs
VG        #PV #LV #SN Attr   VSize  VFree
ubuntu-vg   1   1   0 wz--n- 13.14g 3.14g

vgrename ubuntu-vg ubuntu-otus
Volume group "ubuntu-vg" successfully renamed to "ubuntu-otus"

vgs
VG          #PV #LV #SN Attr   VSize  VFree
ubuntu-otus   1   1   0 wz--n- 13.14g 3.14g

правим /boot/grub/grub.cfg
nano /boot/grub/grub.cfg
меняем ubuntu--vg на ubuntu--otus

vgs
VG          #PV #LV #SN Attr   VSize  VFree
ubuntu-otus   1   1   0 wz--n- 13.14g 3.14g
