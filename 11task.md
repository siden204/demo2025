Вся настройка будет происходить на сервере HQ-SRV\
Первым делом необходимо установить пакеты для dns командой\
apt install bind9 dnsutils\
где:\
bind9 — пакеты для создания dns сервера\
dnsutils — дополнительные пакеты, которые помогут проверить работоспособность (команда host)\
Следующим шагом необходимо создать зоны для прямого и обратного просмотра dns\
Для этого переходим по пути nano /etc/bind/named.conf.default-zones и создаём зоны как показано на скриншотах ниже\

зоны для hq.work(На скриншоте указаны 2 обратные зоны, т. к. у HQ-CLI и HQ-SRV IP-адреса\
заканчиваются на одинаковые октеты и из-за этого DNS может не работать)\
![image](https://github.com/user-attachments/assets/55804138-49d9-4288-a652-7756027b9daa)

zone — создаваемая зона\
type — выбор между первичным и вторичным dns. (Master и Slave)\
file — расположение конфигурационного файла зоны\
allow-update — разрешение динамических обновлений\
где zone:\
hq.work — зона прямого просмотра\
in-addr.arpa — зона обратного просмотра ipv4\

Следующим шагом необходимо создать конфигурационные вайлы для наших зон. Это можно сделать, скопировав стандартные шаблоны командой cp\
Пример:\
cp /etc/bind/db.local /etc/bind/au-team.irpo — создание файла для прямой зоны\
cp /etc/bind/db.127 /etc/bind/ au-team.irpo_obr — создание обратной зоны ipv4\

Первым шагом сконфигурируем зону прямого просмотра, переходим по пути\
nano /etc/bind/au-team.irpo и конфигурируем файл как показано на скриншоте ниже
![image](https://github.com/user-attachments/assets/e8ea309e-6302-491e-82f7-7d7d65136845)\
Где:\
NS запись — обозначение сервера отвественного за разрешение запросов к dns\
A запись — основная запись для зоны прямого просмотра по протоколу ipv4\
CNAME — необязательный параметр, для указания альтернативного имени записи\

Вторым шагом настроим зону обратного просмотра как указано на скриншоте ниже
Зона находится по пути 
nano /etc/bind/au-team.irpo_obr
Рисунок 28— настройка зоны обратного просмотра hq.work для ipv4\
![image](https://github.com/user-attachments/assets/59dbd424-6e88-4491-a72c-29a9b637860a)


настройка второй зоны обратного просмотра hq.work для ipv4\
![image](https://github.com/user-attachments/assets/61652591-f526-4422-804d-deb32460cd0d)

Где:\
PTR запись — основная запись для зоны обратного просмотра\
Проверка выполняется посредством команд\
host IP-адрес\
host имя машины\


