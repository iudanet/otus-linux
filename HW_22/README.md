# VPN

## Домашнее Задание

```txt
VPN
1. Между двумя виртуалками поднять vpn в режимах
- tun
- tap
Прочуствовать разницу.

2. Поднять RAS на базе OpenVPN с клиентскими сертификатами, подключиться с локальной машины на виртуалку

3*. Самостоятельно изучить, поднять ocserv и подключиться с хоста к виртуалке 
```

## Режим tun

### Настройка стенда

```bash
source venv/bin/activate
make install-tun
```

```bash
[vagrant@client ~]$ iperf3 -c 10.10.10.1 -p 5001 -i 2 -t 10
Connecting to host 10.10.10.1, port 5001
[  4] local 10.10.10.2 port 44468 connected to 10.10.10.1 port 5001
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-2.00   sec  44.1 MBytes   185 Mbits/sec   23    525 KBytes       
[  4]   2.00-4.01   sec  48.3 MBytes   202 Mbits/sec    0    626 KBytes       
[  4]   4.01-6.01   sec  48.7 MBytes   204 Mbits/sec    1    505 KBytes       
[  4]   6.01-8.00   sec  45.3 MBytes   191 Mbits/sec  456    314 KBytes       
[  4]   8.00-10.00  sec  47.8 MBytes   200 Mbits/sec    0    410 KBytes       
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec   234 MBytes   196 Mbits/sec  480             sender
[  4]   0.00-10.00  sec   233 MBytes   195 Mbits/sec                  receiver

iperf Done.
[vagrant@client ~]$ ip link show 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
    link/ether 52:54:00:4d:77:d3 brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
    link/ether 08:00:27:d4:97:46 brd ff:ff:ff:ff:ff:ff
8: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN mode DEFAULT group default qlen 100
    link/none 
```

## Режим tap

### Настройка стенда

```bash
source venv/bin/activate
make install-tap
```

```bash
[vagrant@client ~]$ iperf3 -c 10.10.10.1 -p 5001 -i 2 -t 10
Connecting to host 10.10.10.1, port 5001
[  4] local 10.10.10.2 port 44464 connected to 10.10.10.1 port 5001
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-2.01   sec  45.3 MBytes   189 Mbits/sec    0    884 KBytes       
[  4]   2.01-4.01   sec  48.4 MBytes   203 Mbits/sec    0    884 KBytes       
[  4]   4.01-6.01   sec  49.0 MBytes   205 Mbits/sec    0    884 KBytes       
[  4]   6.01-8.00   sec  48.8 MBytes   205 Mbits/sec    0    884 KBytes       
[  4]   8.00-10.00  sec  45.1 MBytes   189 Mbits/sec    0    884 KBytes       
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec   237 MBytes   198 Mbits/sec    0             sender
[  4]   0.00-10.00  sec   236 MBytes   198 Mbits/sec                  receiver
iperf Done.
[vagrant@client ~]$ ip link show 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
    link/ether 52:54:00:4d:77:d3 brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
    link/ether 08:00:27:d4:97:46 brd ff:ff:ff:ff:ff:ff
7: tap0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN mode DEFAULT group default qlen 100
    link/ether ba:d4:43:f9:78:43 brd ff:ff:ff:ff:ff:ff
```

## Заметная разница

Видна разницу в количестеве retray. Для tap режима ровно нулю.
