# Выполнение первой части задания

1. Используйте команды операционной системы Linux и создайте две новых директории – «Игрушки для школьников» и «Игрушки для дошколят»  
```powershell

Welcome to Ubuntu 22.04.1 LTS (GNU/Linux 5.19.0-32-generic x86_64)
* Documentation:  https://help.ubuntu.com
* Management:     https://landscape.canonical.com
* Support:        https://ubuntu.com/advantage

* Introducing Expanded Security Maintenance for Applications.
    Receive updates to over 25,000 software packages with your
    Ubuntu Pro subscription. Free for personal use.

    https://ubuntu.com/pro

0 updates can be applied immediately.


The list of available updates is more than a week old.
To check for new updates run: sudo apt update
Last login: Thu Mar  2 09:56:56 2023

vm@vubu:~$ mkdir Игрушки_для_дошколят
vm@vubu:~$ mkdir Игрушки_для_Школьников
```
2. Создайте в директории «Игрушки для школьников» текстовые файлы - «Роботы», «Конструктор», «Настольные игры»

```powershell
vm@vubu:~$ cd Игрушки_для_Школьников
vm@vubu:~/Игрушки_для_Школьников$ > Роботы
vm@vubu:~/Игрушки_для_Школьников$ > Конструктор
vm@vubu:~/Игрушки_для_Школьников$ > Настольные_Игры
```
3. Создайте в директории «Игрушки для дошколят» текстовые файлы «Мягкие игрушки», «Куклы», «Машинки»

```powershell 
vm@vubu:~/Игрушки_для_Школьников$ cd ..
vm@vubu:~$ cd Игрушки_для_дошколят
vm@vubu:~/Игрушки_для_дошколят$ > Мягкие_Игрушки
vm@vubu:~/Игрушки_для_дошколят$ > Куклы
vm@vubu:~/Игрушки_для_дошколят$ > Машинки
```
4. Объединить 2 директории в одну «Имя Игрушки»  
*Здесь я наперед выполняю задачу под номером **7***
```powershell
vm@vubu:~/Игрушки_для_дошколят$ cd
vm@vubu:~$ sudo snap install tree
[sudo] password for vm:
tree 1.8.0+pkg-3fd6 from 林博仁(Buo-ren, Lin) (brlin) installed
vm@vubu:~$ tree
vm@vubu:~$ mkdir Имя_Игрушки
vm@vubu:~$ mv Игрушки_для_Школьников/ Игрушки_для_дошколят/ Имя_Игрушки/
vm@vubu:~$ cd Имя_Игрушки
vm@vubu:~/Имя_Игрушки$ tree
```
5. Переименовать директорию «Имя Игрушки» в «Игрушки»
```powershell
vm@vubu:~/Имя_Игрушки$ cd
vm@vubu:~$ mv Имя_Игрушки/ Игрушки
vm@vubu:~$ ls
```
6. Просмотреть содержимое каталога «Игрушки».
```powershell
vm@vubu:~$ cd Игрушки
vm@vubu:~/Игрушки$ tree -g
```
7. Установить и удалить snap-пакет. (Любой, какой хотите)  
*Установка пакета была в пункте **4***
```powershell
vm@vubu:~/Игрушки$ sudo snap remove tree
tree removed
```
8. Добавить произвольную задачу для выполнения каждые 3 минуты  
(Например, запись в текстовый файл чего-то или копирование из каталога А в каталог Б).
```powershell
vm@vubu:~/Игрушки$ sudo vi /usr/local/bin/script.sh
    #!/bin/bash
    echo $(date) >> /var/log/testcron.log
    :w!
    :q
vm@vubu:~/Игрушки$ sudo chmod ugo+x /usr/local/bin/script.sh
vm@vubu:~/Игрушки$ sudo crontab -e
    0/3 * * * * /usr/local/bin/script.sh
crontab: installing new crontab