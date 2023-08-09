
# Intervlan Routing

Pada tutorial ini menjelaskan tentang Intervlan Routing pada 3 switch menggunakan cisco packet tracer.

- Hubungkan komputer dengan switch dengan kabel console.
- masuk ke global configuration mode, buat nama switch, dan buat password. 
```bash
  Switch>enable
  Switch#configure terminal
  Switch(config)# hostname SW-Gedung-A
  SW-Gedung-A(config)#enable secret ciscotel
  SW-Gedung-A(config)#line console 0
  SW-Gedung-A(config-line)#password ciscocon
  SW-Gedung-A(config-line)#login
  SW-Gedung-A(config-line)#exit
```
- Lakukan hal yang sama pada switch Gedung B
```bash
  Switch>enable
  Switch#configure terminal
  Switch(config)# hostname SW-Gedung-B
  SW-Gedung-B(config)#enable secret ciscotel
  SW-Gedung-B(config)#line console 0
  SW-Gedung-B(config-line)#password ciscocon
  SW-Gedung-B(config-line)#login
  SW-Gedung-B(config-line)#exit
```
- Buat konfigurasi vlan pada switch sesuai dengan port yang diinginkan
```bash
  SW-Gedung-A(config)#vlan 10
  SW-Gedung-A(config-vlan)#name lantai1
  SW-Gedung-A(config-vlan)#vlan 20
  SW-Gedung-A(config-vlan)#name lantai2
  SW-Gedung-A(config-vlan)#vlan 30
  SW-Gedung-A(config-vlan)#name lantai3
  SW-Gedung-A(config-vlan)#exit
  SW-Gedung-A(config)#interface range fastEthernet 0/1-10
  SW-Gedung-A(config-if-range)# switchport mode access
  SW-Gedung-A(config-if-range)# switchport access vlan 10
  SW-Gedung-A(config-if-range)#exit
  SW-Gedung-A(config)#interface range fastEthernet 0/11-20
  SW-Gedung-A(config-if-range)# switchport mode access
  SW-Gedung-A(config-if-range)# switchport access vlan 20
  SW-Gedung-A(config-if-range)#exit
  SW-Gedung-A(config)#interface range fastEthernet 0/21-24
  SW-Gedung-A(config-if-range)# switchport mode access
  SW-Gedung-A(config-if-range)# switchport access vlan 30
  SW-Gedung-A(config-if-range)#exit
```
- Lakukan configurasi yang sama pada Switch Gedung B
```bash
  SW-Gedung-B(config)#vlan 10
  SW-Gedung-B(config-vlan)#name lantai1
  SW-Gedung-B(config-vlan)#vlan 20
  SW-Gedung-B(config-vlan)#name lantai2
  SW-Gedung-B(config-vlan)#vlan 30
  SW-Gedung-B(config-vlan)#name lantai3
  SW-Gedung-B(config-vlan)#exit
  SW-Gedung-B(config)#interface range fastEthernet 0/1-10
  SW-Gedung-B(config-if-range)# switchport mode access
  SW-Gedung-B(config-if-range)# switchport access vlan 10
  SW-Gedung-B(config-if-range)#exit
  SW-Gedung-B(config)#interface range fastEthernet 0/11-20
  SW-Gedung-B(config-if-range)# switchport mode access
  SW-Gedung-B(config-if-range)# switchport access vlan 20
  SW-Gedung-B(config-if-range)#exit
  SW-Gedung-B(config)#interface range fastEthernet 0/21-24
  SW-Gedung-B(config-if-range)# switchport mode access
  SW-Gedung-B(config-if-range)# switchport access vlan 30
  SW-Gedung-B(config-if-range)#exit
```
- Masukkan IP address pada tiap masing masing PC
```bash
  - Untuk switch gedung A IP address dimulai dari 
  IPv4 Address = 192.168.10.2,
  Subnet Mask = 255.255.255.0,
  Default Gateway = 192.168.10.1 
  - Untuk switch gedung B IP address dimulai dari 
  IPv4 Address= 192.168.10.102,
  Subnet Mask = 255.255.255.0,
  Default Gateway = 192.168.10.101
```
- Supaya vlan pada switch gedung A dan gedung B terkoneksi maka buat switch menjadi mode trunk
```bash
  SW-Gedung-A(config)#interface gigabitEthernet 0/1
  SW-Gedung-A(config-if-range)# switchport mode trunk
  SW-Gedung-A(config-if-range)#exit
```
-Lakukan hal yang sama pada switch gedung B
```bash
  SW-Gedung-B(config)#interface gigabitEthernet 0/1
  SW-Gedung-B(config-if-range)# switchport mode trunk
  SW-Gedung-B(config-if-range)#exit
```
- Lakukan ping antar pc melalui command prompt
- Jika pc dengan vlan yang sama succes lalu jika pc dengan vlan yang berbeda tidak saling terhubung atau Request time out pada saat ping di command prompt maka konfigurasi antar vlan telah berhasil.


