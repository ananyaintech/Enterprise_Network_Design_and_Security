# Configuration Commands

## VLAN Configuration

```bash
enable
configure terminal

vlan 10
name HR

vlan 20
name Finance

vlan 30
name IT
```

---

## Access Port Configuration

```bash
interface fa0/1
switchport mode access
switchport access vlan 10

interface fa0/2
switchport mode access
switchport access vlan 20

interface fa0/3
switchport mode access
switchport access vlan 30
```

---

## Trunk Configuration

```bash
interface fa0/24
switchport mode trunk
```

---

## Inter-VLAN Routing (Router-on-a-Stick)

```bash
interface g0/0.10
encapsulation dot1Q 10
ip address 192.168.10.1 255.255.255.0

interface g0/0.20
encapsulation dot1Q 20
ip address 192.168.20.1 255.255.255.0

interface g0/0.30
encapsulation dot1Q 30
ip address 192.168.30.1 255.255.255.0
```

---

## DHCP Configuration

```bash
ip dhcp excluded-address 192.168.10.1

ip dhcp pool HR
network 192.168.10.0 255.255.255.0
default-router 192.168.10.1
dns-server 192.168.10.50

ip dhcp pool FINANCE
network 192.168.20.0 255.255.255.0
default-router 192.168.20.1
dns-server 192.168.10.50

ip dhcp pool IT
network 192.168.30.0 255.255.255.0
default-router 192.168.30.1
dns-server 192.168.10.50
```

---

## OSPF Configuration

```bash
router ospf 1

network 192.168.10.0 0.0.0.255 area 0
network 10.0.12.0 0.0.0.3 area 0
```

---

## ACL Configuration

```bash
access-list 100 deny ip 192.168.10.0 0.0.0.255 192.168.20.0 0.0.0.255

access-list 100 permit ip any any

interface g0/0
ip access-group 100 in
```

---

## SSH Configuration

```bash
hostname HQ-Router

ip domain-name company.com

username admin secret Cisco123

crypto key generate rsa

line vty 0 4
login local
transport input ssh
```

---

## Verification Commands

```bash
show vlan brief

show ip interface brief

show ip dhcp binding

show ip ospf neighbor

show ip route

show access-lists

show running-config
```
