### Настройка ISP

iptables:\
apt-get install iptables iptables-persistent\
Затем нужно создать правила iptables\
iptables –t nat –A POSTROUTING –s 172.16.4.0/28 –o ens192 –j MASQUERADE\
iptables –t nat –A POSTROUTING –s 172.16.5.0/28 –o ens192 –j MASQUERADE\
iptables-save > /etc/iptables/rules.v4

Перезапускаем iptables: systemctl restart iptables\
Для проверки вводим команду iptables –L –t nat\
После настройки на интерфейсах ISP может слететь Ip.\

Также на роутерах и ISP нужно зайти в файл\
/etc/sysctl.conf и раскомментировать строку «net.ipv4.ip_forward=0» и привести её к виду «net.ipv4.ip_forward=1».

Также для работы nat и доступа в интернет на роутерах в качестве gateway указать адрес ISP.

### На HQ-RTR и BR-RTR

Нужно зайти в файл /etc/resolv.conf и оставить там только одну строку: nameserver 1.1.1.1

![image](https://github.com/user-attachments/assets/74af8421-96f1-4c8f-8272-0b6477054cf7)

