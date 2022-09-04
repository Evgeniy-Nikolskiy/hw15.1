# Homework 15.1  

Деплоим:
```
...
Apply complete! Resources: 7 added, 0 changed, 0 destroyed.

public_nat_ip = "84.201.129.17"
test_private_ip = "192.168.20.30"
test_public_ip = "84.201.156.124"
```

Тестируем. Заходим на виртуалку в публичной подсети, убеждаемся что есть выход в интернет, проверяем внешний IP:
```
$ ssh -A cloud-user@51.250.67.191
[cloud-user@test-public-vm ~]$ curl ifconfig.co
51.250.67.191
```
Оттуда заходим на виртуалку в приватной подсети, убеждаемся что есть выход в интернет, проверяем внешний IP:
```
[cloud-user@test-public-vm ~]$ ssh 192.168.20.18
[cloud-user@test-private-vm ~]$ curl ifconfig.co
51.250.67.117
```

Пробуем подключиться напрямую к этому адресу:
```
$ ssh ubuntu@51.250.67.117
Welcome to Ubuntu 18.04.1 LTS (GNU/Linux 4.15.0-29-generic x86_64)
#################################################################
This instance runs Yandex.Cloud Marketplace product
Please wait while we configure your product...

Documentation for Yandex Cloud Marketplace images available at https://cloud.yandex.ru/docs

#################################################################
...
ubuntu@nat-instance:~$ 
```
Попадаем внутрь nat-инстанса.