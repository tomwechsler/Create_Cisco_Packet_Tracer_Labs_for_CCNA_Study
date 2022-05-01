Switch starter configuration
----------------------------

enable
config t
hostname OfficeSwitch
no ip domain-lookup								(ausschalten der Namensauflösung)
ip domain-name prime.pri
username admin secret cisco
enable secret cisco
crypto key generate rsa general-keys modulus 1024
ip ssh v 2
line con 0
login local
logging synchronous
line vty 0 4
login local
logging synchronous
transport input ssh
int range f0/1 - 24 , g0/1 - 2
switchport access vlan 10
switchport nonegotiate
spanning-tree portfast

interface vlan 10
ip address 10.10.0.2 255.255.255.0
no shutdown

copy running-config startup-config

ip default-gateway 10.10.0.1

Router Starter-Konfiguration
----------------------------
enable
config t
hostname MainRouter
no ip domain-lookup
ip domain-name prime.pri
username admin secret cisco
enable secret cisco
crypto key generate rsa general-keys modulus 1024
ip ssh v 2
line con 0
login local
logging synchronous
line aux 0
login local
logging synchronous
line vty 0 4
login local
logging synchronous
transport input ssh
interface f0/0
ip address 10.10.0.1 255.255.255.0
no shutdown
interface f0/1
ip address 10.20.0.1 255.255.255.0
no shutdown

copy running-config startup-config


