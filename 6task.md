 Реализация GRE-туннеля между офисами

Нужно зайти в файл /etc/modules и добавить там строку ip_gre:

![image](https://github.com/user-attachments/assets/05b2d8d6-36ff-477c-9de1-454303b496a8)


Вся последующая настройка проводится в файле /etc/network/interfaces

![image](https://github.com/user-attachments/assets/16034424-0086-48fd-ba17-f81adce683d5)


Рисунок 14 - Настройка GRE на HQ-RTR

![image](https://github.com/user-attachments/assets/5142fcaf-cc21-4e6c-a895-bf01d0e09241)

Рисунок 15 - Настройка GRE на BR-RTR
Ping 10.10.0.1 и ping 10.10.0.2 для проверки работоспособности туннеля с обеих сторон:

![image](https://github.com/user-attachments/assets/e4e9463c-97f4-4fda-a81d-f8ba2181f3bc)
рисунок проверки работоспособности


