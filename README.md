# demo2025
демка сетевое и системное администрирование 

-------------------------------------------

### имена устройств

ISP: hostnamectl set-hostname isp.au-team.irpo\
HQ-RTR hostnamectl set-hostname hq-rtr.u-team.irpo\
HQ-CLI: hostnamectl set-hostname hq-cli.au-team.irpo\
HQ-SRV hostnamectl set-hostname hq-srv.au-team.irpo\
BR-RTR hostnamect set-hostname br-rtr.au-team.irpo\
BR-SRV hostnamectl set-hostname br-srv.au-team.irpo

### -----ISP----

nano /etc/network/interfaces

auto ens192\
iface ens192 inet static\
address 172.16.4.1  
netmask 255.255.255.240

auto ens224  
iface ens224 inet static  
address 172.16.5.1  
netmask 255.255.255.240



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

#auto ens224:1  
#iface ens224:1 inet static  
     #address 192.168.200.1  
     #netmask 255.255.255.240  

#auto ens224:100  
#iface ens224:100 inet static  
    #address 102.168.100.3  
    #netmask 255.255.255.240  
#vlan-raw-device ens224:100  

#auto ens224:200  
#iface ens224:200 inet static  
    #address 192.168.200.3  
    #netmask 255.255.255.240  
#vlan-raw-device ens224:200  


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
#auto gre1
#iface gre1 inet tunnel
#address 172.0.2
#netmask 255.255.255.252
#mode gre
#local 172.16.4.2
#ttl 64



### ------------------BR-SRV-----------------------

nano  /etc/network/interfaces\
auto eth0\
iface eth0 inet static\
    address 192.168.0.2\
    netmask 255.255.255.224\
    gateway 192.168.0.1\

на всех устройствах чекать файл\
nano /etc/sysctl.conf\
nano /etc/apt/sources.list
nano /etc/resolv.4
