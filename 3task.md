### Создание учёток sshuser производится на HQ-SRV и BR-SRV

adduser sshuser -u 1010 -U
passwd sshuser
P@ssw0rd

ВЫДАЕМ ROOT права\
user -aG sudo sshuser

Добавляем следующую строку в /etc/sudoers:\
sshuser ALL=(ALL) NOPASSWD:ALL


Создаем и задаем необходимые права на домашнюю папку\
mkdir /home/sshuser\
chown sshuser:sshuser /home/sshuser\
chmod 700 /home/sshuser

----------------------------------------------

### Пользователь net_admin на HQ-RTR и BR-RTR
useradd net_admin
passwd net_admin
P@ssw0rd

usermod -aG sudo net_admin

net_admin ALL=(ALL) NOPASSWD :ALL

mkdir /home/net_admin
chown net_admin:net_admin /homenet_admin
chmod 700 /home/net_admin
