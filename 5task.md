5. Настройка безопасного удалённого доступа

Первым делом необходимо перейти по пути nano /etc/ssh/sshd_config где\
в окне конфигурации нам необходимо на HQ-SRV найти строки и изменить значения как указанно на рисунке 10\

![image](https://github.com/user-attachments/assets/f7d81de6-4748-40f0-a42c-81854cce9956)


![image](https://github.com/user-attachments/assets/14bd2108-1ea9-4e56-9394-5f25c91a5722)


Рисунок 11— Ограничение попыток авторизации\
![image](https://github.com/user-attachments/assets/ffed0cdb-59f8-4d17-a924-55fc2f9d5544)


Для настройки баннера нужно зайти в файл /etc/ssh-banner и написать следующее: Authorized acces only

![image](https://github.com/user-attachments/assets/4d704740-64ae-4c4e-9be6-ccd856a72b90)


Для применения конфигурации необходимо перезагрузить службу командой systemctl restart ssh
Для проверки доступа нужно написать команду: ssh sshuser@192.168.100.2 -p 2024
Где -p — указание порта. Без указания порта подключится не получится
Также, при неправильном вводе пароля должно вывестись сообщение баннера

