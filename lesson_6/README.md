# Загрузка системы

## Домашнее задание

1. Попасть в систему без пароля несколькими способами
2. Установить систему с LVM, после чего переименовать VG
3. Добавить модуль в initrd

___Операции происходят на установке Centos8 minimal___

### 1. Попасть в систему без пароля несколькими способами


#### Способ 1. init=/bin/sh

* При загрузке в Grub, выбираем нужное ядро, нажимаем **e**
* в конце строки начинающейся на linux вбиваем ```init=/bin/sh``` и нажимаем **ctr+x** для загрузки
![grub1](img/grub_1.png)
* после загрузки сразу получаем shell
![shell1](img/shell_1.png)
* Перемонтируем ФС в RW режим и пробуем что то записать на диск

    ```bash
    mount -o remount,rw /
    mount | grep root
    ```

    ![example1](img/example_1.png)

#### Способ 2. rd.break

* При загрузке в Grub, выбираем нужное ядро, нажимаем **e**
* в конце строки начинающейся на linux вбиваем ```rd.break``` и нажимаем **ctr+x** для загрузки
![grub2](img/grub_2.png)
* Получаем shell
![shell2](img/shell_2.png)
* выполняем комманды:
  * монтируем в RW режим ситсему: ```mount -o remount,rw /sysroot```
  * Делаем chroot: ```chroot /sysroot```
  * Меняем пароль root: ```passwd root```
  * запуск autorelabeling при загрузке: ```touch /.autorelabel```
![example2](img/example_2.png)
* Перезагружаемся, дожидаемся завершения autorelabeling
![relable](img/relable.png)
* входим под новым паролем root.

#### Способ 3. rw init=/sysroot/bin/sh

* При загрузке в Grub, выбираем нужное ядро, нажимаем **e**
* в конце строки начинающейся на linux вбиваем вместо ```ro``` ``` rw init=/sysroot/bin/sh``` и нажимаем **ctr+x** для загрузки
![grub3](img/grub_3.png)
* После загрузки получаем shell
![shell3](img/shell_3.png)
* выполняем комманды:
  * Делаем chroot: ```chroot /sysroot```
  * Меняем пароль root: ```passwd root```
  * запуск autorelabeling при загрузке: ```touch /.autorelabel```
![example2](img/example_3.png)
* Перезагружаемся, дожидаемся завершения autorelabeling
* входим под новым паролем root.

## 2. Установить систему с LVM, после чего переименовать VG

## 3. Добавить модуль в initrd