# demo2025
демка сетевое и системное администрирование 

---------------ISP-----------------------
nano /etc/network/interfaces
auto ens192
iface ens192 inet static
    address 172.16.4.1
    netmask 255.255.255.240

auto ens224
iface ens224 inet static
    address 172.16.5.1
    netmask 255.255.255.240
