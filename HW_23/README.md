# DNS

## Домашнее Задание

```txt
настраиваем split-dns
взять стенд https://github.com/erlong15/vagrant-bind
добавить еще один сервер client2
завести в зоне dns.lab
имена
web1 - смотрит на клиент1
web2 смотрит на клиент2

завести еще одну зону newdns.lab
завести в ней запись
www - смотрит на обоих клиентов

настроить split-dns
клиент1 - видит обе зоны, но в зоне dns.lab только web1

клиент2 видит только dns.lab

*) настроить все без выключения selinux
Критерии оценки: 4 - основное задание сделано, но есть вопросы
5 - сделано основное задание
6 - выполнено задания со звездочкой 
```

```txt
# Vagrant DNS Lab

A Bind's DNS lab with Vagrant and Ansible, based on CentOS 7.

# Playground

<code>
    vagrant ssh client
</code>

  * zones: dns.lab, reverse dns.lab and ddns.lab
  * ns01 (192.168.50.10)
    * master, recursive, allows update to ddns.lab
  * ns02 (192.168.50.11)
    * slave, recursive
  * client (192.168.50.15)
    * used to test the env, runs rndc and nsupdate
  * zone transfer: TSIG key
```
