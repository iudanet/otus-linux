# BASH

## Домашнее задание

## ВАЖНО

при запуске Vagrantfile  в bootstrap_vm.sh требуется указать email для отправки отчета

## Запуск

```bash
vagrant up
```

## Скрипт

```bash
./script.sh -x 10  -y 30 -f access.log -mail chudo88@gmail.com
```

описание параметров скрипта

* -x : (int) количество IP адресов в отчете
* -y : (int) количество запрашиваемых URI в отчете
* -f : Файл с логами
* -mail : email для отправки

## Прочее

* Скрипт до боевого решения еще развивать и развивать =)
* Почтовый ящик для отправки почты будет существовать до сдачи ДЗ
* С файлом срабатывает 1 раз, если добавить в файл данных, то сработает с последнего места запуска.
* скрипт не обрабатывает возможность уменьшения файла логов или его удаления, в этом случае надо уладить стейт файл ```/tmp/log_parser.tmp```
* на боевом nginx лучше сделать с помощью ротации логов.
  * запускать ротацию в NGINX и спокойно обрабатывать новый файл от начала и до конца без файлов с промежуточным состоянием,
  * в идеале скрип добавить в logrotate и запускать его раз в час вместе с ротацией логов, тогда мы не потеряем отчеты в момент системной ротации логов если скрип будет просто в кроне.
