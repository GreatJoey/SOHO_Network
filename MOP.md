Method of Procedure

R2 Router:
```
enable configure terminal
interface 0/0
no shutdown
!
interface g0/0.10
encapsulation dot1Q 10
ip address 192.168.10.1 255.255.255.0
!
interface g0/0.20
encapsulation dot1Q 20
ip address 192.168.20.1 255.255.255.0
!
interface g0/0.30
encapsulation dot1Q 30
ip address 192.168.30.1 255.255.255.0
!
ip dhcp excluded-address 192.168.10.1 192.168.10.20
ip dhcp excluded-address 192.168.20.1 192.168.20.20
ip dhcp excluded-address 192.168.30.1 192.168.30.20
!
ip dhcp pool ADMIN
network 192.168.10.0 255.255.255.0
default-router 192.168.10.1
dns-server 8.8.8.8
!
ip dhcp pool USERS
network 192.168.20.0 255.255.255.0
default-router 192.168.20.1
dns-server 8.8.8.8
!
ip dhcp pool IOT
network 192.168.30.0 255.255.255.0
default-router 192.168.30.1
dns-server 8.8.8.8
!
interface g0/1
ip address 203.0.113.2 255.255.255.252
no shutdown
!
ip route 0.0.0.0 0.0.0.0 203.0.113.1
show ip route
!
access-list 1 permit 192.168.10.0 0.0.0.255
access-list 1 permit 192.168.20.0 0.0.0.255
access-list 1 permit 192.168.30.0 0.0.0.255
ip nat inside source list 1 interface g0/1 overload
interface g0/0.10
ip nat inside
interface g0/0.20
ip nat inside
interface g0/0.30
ip nat inside
interface g0/1
ip nat outside
```

R1
```
interface g0/0
ip address 203.0.113.1 255.255.255.252
no shutdown
!
interface g0/1
ip address 8.8.8.1 255.255.255.0
no shutdown
```
SW1
```
enable
configure terminal 
!
vlan 10 
name ADMIN
!
vlan 20
name USERS
!
vlan 30 
name IOT
!
interface f0/1
switchport mode access
swichport access vlan 10
!
interface f0/2
switchport mode access
swichport access vlan 20
!
interface f0/3
switchport mode access
switchport access vlan 30
!
interface g0/1
switchport mode trunk
show interfaces trunk
```