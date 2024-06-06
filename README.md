# Jarkom-Modul-4-IT27-2024

| Nama | NRP |
| ---------------------- | ---------- |
| Azzahra Sekar Rahmadina | 5027221035 |
| Zulfa Hafizh Kusuma | 5027221038 |

# List of Contents
- [Official Report](#official-report)
  - [List of Contents](#list-of-contents)
  - [Topology](#topology)
  - [Prefix IP](#prefix-ip)
  - [Rute](#rute)
  - [VLSM](#vlsm)
  - [CIDR](#cidr)

# Topology

## GNS3 VLSM

![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/128958228/5b1a08a0-87e7-450f-a73b-7e9bd87a8b25)

## CPT CIDR

# PREFIX IP

Kelompok kami menggunakan prefix IP `10.77`

# RUTE

Setelah melakukan riset dan melakukan percobaan, diperoleh hasil dari rute yang kami dapatkan adalah sebagai berikut: 

![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/128958228/ce61010e-bed5-416d-bf37-d9e2d9c3552d)

# VLSM

## Tree

Berikut merupakan hasil pemecahan subnet besar yang akan dibentuk menjadi jaringan yang lebih kecil

![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/128958228/ea0da3b6-dff1-4813-aa64-c74a926104e4)

## Pembagian IP

Berikut adalah hasil dari pembagian IP yang telah kami peroleh dari hasil pemecahan tadi menjadi jaringan yang lebih kecil: 

![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/128958228/e4d7613d-a384-45c5-a287-a97bda0c928f)

## Konfigurasi

- **Router**
  - Jawa
    ```bash
    auto lo
    iface lo inet loopback

    auto eth0
    iface eth0 inet dhcp

    #A1 Jawa-Sulawesi
    auto eth1
    iface eth1 inet static
      address 10.77.21.181
      netmask 255.255.255.252

    #A7 Jawa-Kalimantan
    auto eth2
    iface eth2 inet static
      address 10.77.21.185
      netmask 255.255.255.252

    #A15 Jawa-Sumatera
    auto eth3
    iface eth3 inet static
      address 10.77.21.177
      netmask 255.255.255.252
    ```
  - Sumatra
    ```bash
    auto lo
    iface lo inet loopback

    #A15 > JAWA
    auto eth0
    iface eth0 inet static
      address 10.77.21.178
      netmask 255.255.255.252
      gateway 10.77.21.177

    #A16 > SW-TOBA
    auto eth1
    iface eth1 inet static
      address 10.77.21.65
      netmask 255.255.255.224

    #A20 > LAMPUNG
    auto eth2
    iface eth2 inet static
      address 10.77.21.205
      netmask 255.255.255.252
    ```
  - Sulawesi
    ```bash

    ```
  - Sumatera-utara
    ```bash

    ```
  - Kalimantan
    ```bash

    ```
  - Kalimantan Utara
    ```bash

    ```
  - Kalimantan Selatan
    ```bash

    ```
  - Kalimantan Timur
    ```bash

    ```

## Routing
  - Jawa
    ```bash
    # Sul
    route add -net 10.77.21.168 netmask 255.255.255.248 gw 10.77.21.182
    route add -net 10.77.21.160 netmask 255.255.255.248 gw 10.77.21.182
    route add -net 10.77.20.128 netmask 255.255.255.128 gw 10.77.21.182
    route add -net 10.77.21.0 netmask 255.255.255.192 gw 10.77.21.182
    route add -net 10.77.8.0 netmask 255.255.248.0 gw 10.77.21.182

    # Kal
    route add -net 10.77.21.188 netmask 255.255.255.252 gw 10.77.21.186
    route add -net 10.77.18.0 netmask 255.255.255.0 gw 10.77.21.186
    route add -net 10.77.21.192 netmask 255.255.255.252 gw 10.77.21.186
    route add -net 10.77.21.196 netmask 255.255.255.252 gw 10.77.21.186
    route add -net 10.77.16.0 netmask 255.255.254.0 gw 10.77.21.186
    route add -net 10.77.21.96 netmask 255.255.255.224 gw 10.77.21.186
    route add -net 10.77.0.0 netmask 255.255.248.0 gw 10.77.21.186

    # Sum
    route add -net 10.77.21.64 netmask 255.255.255.224 gw 10.77.21.182
    route add -net 10.77.21.200 netmask 255.255.255.252 gw 10.77.21.182
    route add -net 10.77.20.0 netmask 255.255.255.128 gw 10.77.21.182
    route add -net 10.77.21.204 netmask 255.255.255.252 gw 10.77.21.182
    route add -net 10.77.21.128 netmask 255.255.255.224 gw 10.77.21.182
    route add -net 10.77.19.0 netmask 255.255.255.0 gw 10.77.21.182
    ```
  - Sulawesi
    ```bash

    ```
  - Sumatera
    ```bash

    ```
  - Sumatera-utara
    ```bash

    ```
  - Kalimantan
    ```bash

    ```
  - Kalimantan Utara
    ```bash

    ```
  - Kalimantan Selatan
    ```bash

    ```
  - Kalimantan Timur
    ```bash

    ```
