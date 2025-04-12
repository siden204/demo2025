# demo2025
демка сетевое и системное администрирование 

### -----ISP----

nano /etc/network/interfaces

auto ens192  
iface ens192 inet static  
address 172.16.4.1  
netmask 255.255.255.240

auto ens224  
iface ens224 inet static  
address 172.16.5.1  
netmask 255.255.255.240


#### перед настройкой HQ-RTR  
apt install vlan  
modprobe 8021q  
echo 8021q | sudo tee -a /etc/modules  

### --------------------HQ-RTR---------------------

nano /etc/network/interfaces  
auto ens192  
iface ens192 inet static  
    address 172.16.4.2  
    netmask 255.255.255.240  
    gateway 172.16.4.1  

auto ens224  
iface ens224 inet static  
    address 192.168.100.1  
    netmask 255.255.255.192  

auto ens224:1  
iface ens224:1 inet static  
    address 192.168.200.1  
    netmask 255.255.255.240  

auto ens224:100  
iface ens224:100 inet static  
    address 102.168.100.3  
    netmask 255.255.255.240  
vlan-raw-device ens224:100  

auto ens224:200  
iface ens224:200 inet static  
    address 192.168.200.3  
    netmask 255.255.255.240  
vlan-raw-device ens224:200  


#### Настройка маршрутов
up route add -net 192.168.100.0 netmask 255.255.255.192 gw 192.168.200.1\
up route add -net 192.168.0.0 netmask 255.255.255.224 gw 172.16.5.1



### --------------------HQ-SRV---------------------


nano /etc/network/interfaces\
auto ens192\
iface ens192 inet static\
    address 192.168.100.2\
    netmask 255.255.255.192\
    gateway 192.168.100.1



### -------------------------HQ-CLI---------------------
nano /etc/network/interfaces\
auto ens192\
iface ens192 inet static\
    address 192.168.100.3\
    netmask 255.255.255.240\
    gateway 192.168.100.1\





### -------------------------BR-RTR---------------------

nano  /etc/network/interfaces\
auto ens192\
iface ens192 inet static\
    address 172.16.5.2\
    netmask 255.255.255.240\
    gateway 172.16.5.1\

auto ens224\
iface ens224 inet static\
    address 192.168.0.1\
    netmask 255.255.255.224\

#### Настройка маршрутов
up route add -net 192.168.200.0 netmask 255.255.255.240 gw 192.168.0.1




### ------------------BR-SRV-----------------------

nano  /etc/network/interfaces\
auto eth0\
iface eth0 inet static\
    address 192.168.0.2\
    netmask 255.255.255.224\
    gateway 192.168.0.1\






### НАСТРОЙКА ISP

apt-get install iptables iptables-persistent



