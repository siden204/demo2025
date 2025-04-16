### Настройте автоматическое распределение IP-адресов на роутере HQ-R. 

Учтите, что у сервера должен быть зарезервирован адрес.\
Первым шагом необходимо на машине HQ-R установить dhcp server командой\
apt install isc-dhcp-server\
После установки пакета следующим шагом необходимо сконфигурировать файл для указания\
интерфейсов прослушивания DHCP сервера зайти можно с помощью команды

nano /etc/default/isc-dhcp-server
и настроить интерфейс, направленный в сторону клиента, если в сети подразумевается DHCP-relay, то 2 интерфейса в сторону клиента,\
и в сторону сети откуда исходит запрос. Строка v6 закоментирована, чтобы DHCP даже не думал пробовать его раздавать

Указание интерфейса для передачи адреса\
![image](https://github.com/user-attachments/assets/1d8317e9-871c-42c4-b0f7-3251ad9f3874)


Далее необходимо настроить 2 конфигурационных файла для IPv4 для IPv6\
Которые можно найти по путям nano /etc/dhcp/dhcpd.conf и nano /etc/dhcp/dhcpd6.conf соответственно

Пример настройки DHCP для ipv4 без Relay\
![image](https://github.com/user-attachments/assets/25ae9a2b-96ce-4653-b353-57718ed93c83)

ddns-update-style interim — способ автообновления базы dns\
authoritative — делает сервер доверенным\
subnet — указание сети\
range — пул адресов\
option routers — шлюз по умолчанию  

Перезапускаем службу DHCP: systemctl restart isc-dhcp-server\
Для проверки на HQ-CLI нужно указать получение адреса по DHCP\
![image](https://github.com/user-attachments/assets/b5a9d31e-48e3-4ad3-b259-f99ab6449421)

Прописываем systemctl restart networking для применения и проверяем выданный ip-адрес командой ip -c a\
Проверка выдачи ip-адреса\
![image](https://github.com/user-attachments/assets/8adaf46c-3313-49fd-a17f-fdd26b7a1933)













