# Iptebles

## Домашнее задание

```txt
ценарии iptables
1) реализовать knocking port
- centralRouter может попасть на ssh inetrRouter через knock скрипт
пример в материалах
2) добавить inetRouter2, который виден(маршрутизируется (host-only тип сети для виртуалки)) с хоста или форвардится порт через локалхост
3) запустить nginx на centralServer
4) пробросить 80й порт на inetRouter2 8080
5) дефолт в инет оставить через inetRouter

* реализовать проход на 80й порт без маскарадинга 
```

### Запуск стенда

- установка Ansible

    ```bash
    cd HW_17
    python3.8 -m venv venv
    source venv/bin/activate
    pip install --upgrade pip
    pip install -r requirements.txt
    ```

- Запуск виртуальных машин и настройка окружения. В связи с тем, что странно себя ведет перезагрузка network
  - окружение запускается 13 минут

    ```bash
    make install
    ```

- Запуск теста доступности, проверяет доступность IP  с разных хостов другие
 хосты и интернет + трасировка.
  - тест проверяется минуту

    ```bash
    make test
    ```
