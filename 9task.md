### Настройка динамической трансляции адресов

Точно также как и для ISP устанавливаем пакеты iptables:\
apt install iptables iptables-persistent\
iptables –t nat –A POSTROUTING –s 192.168.100.0/26 –o ens192 –j MASQUERADE  

iptables –t nat –A POSTROUTING –s 192.168.200.0/28 –o ens192 –j MASQUERADE 

#### Правило для BR-RTR\
iptables –t nat –A POSTROUTING –s 192.168.0.0/27 –o ens192 –j MASQUERADE  

Затем эти правила нужно сохранить: iptables-save > /etc/iptables/rules.v4\
После этого перезапускаем службу
