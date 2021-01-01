#

## Домашнее задание

```txt
Домашнее задание
развернуть стенд с веб приложениями в vagrant
Варианты стенда
nginx + php-fpm (laravel/wordpress) + python (flask/django) + js(react/angular)
nginx + java (tomcat/jetty/netty) + go + ruby
можно свои комбинации

Реализации на выбор
- на хостовой системе через конфиги в /etc
- деплой через docker-compose

Для усложнения можно попросить проекты у коллег с курсов по разработке

К сдаче примается
vagrant стэнд с проброшенными на локалхост портами
каждый порт на свой сайт
через нжинкс
```

## Описание

Используются проекты

* https://github.com/iudanet/react-redux-realworld-example-app (React)
* https://github.com/iudanet/flask-realworld-example-app (Python / Flask )
* wordpress (php / php-fpm)

Проэкты разворачиваются через docker-compose

* http://localhost (React + flask)
* http://localhost:8080 (wordpres)

