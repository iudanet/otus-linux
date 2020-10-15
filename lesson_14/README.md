# Docker

## Домашнее задание

```txt
Создайте свой кастомный образ nginx на базе alpine. После запуска nginx должен
отдавать кастомную страницу (достаточно изменить дефолтную страницу nginx)
Определите разницу между контейнером и образом
Вывод опишите в домашнем задании.
Ответьте на вопрос: Можно ли в контейнере собрать ядро?
Собранный образ необходимо запушить в docker hub и дать ссылку на ваш
репозиторий.

Задание со * (звездочкой)
Создайте кастомные образы nginx и php, объедините их в docker-compose.
После запуска nginx должен показывать php info.
Все собранные образы должны быть в docker hub
```

## Описание

* Создать образ Nginx

    ```bash
    cd lesson_14/nginx
    docker build -t iudanet/nginx-otus:0.1 -t iudanet/nginx-otus:latesat .
    docker login -u iudanet
    docker push iudanet/nginx-otus:latesat
    ```

  * Образ доступен по имени ```iudanet/nginx-otus:latesat```
* Определите разницу между контейнером и образом
  * Образ это базовая сущность (артифакт) ,а контейнер создается из образа и является его потомком
* Ответьте на вопрос: Можно ли в контейнере собрать ядро?
  * скомпилировать бинарник можно, запустить нельзя, так как Docker использует хостовое ядро
* Создайте кастомные образы nginx и php, объедините их в docker-compose

```bash
cd lesson_14/nginx-php
docker-compose build
docker-compose up -d
curl 127.0.0.1:8085
```