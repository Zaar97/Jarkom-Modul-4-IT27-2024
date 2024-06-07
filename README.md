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

![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/635eaba2-f333-4976-a2f4-447e9dfda80e)

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
  - Sumatera Utara
    ```bash
    auto lo
    iface lo inet loopback

    #A16 > SW-TOBA
    auto eth0
    iface eth0 inet static
      address 10.77.21.73
      netmask 255.255.255.224
      gateway 10.77.21.65

    #A17 > ACEH
    auto eth1   
    iface eth1 inet static
      address 10.77.21.201
      netmask 255.255.255.252
    ```
  - Kalimantan
    ```bash
    auto lo
    iface lo inet loopback

    #A7 > JAWA
    auto eth0
    iface eth0 inet static
      address 10.77.21.186
      netmask 255.255.255.252
      gateway 10.77.21.185

    #A8 > KALIMANTAN-UTARA
    auto eth1
    iface eth1 inet static
      address 10.77.21.189
      netmask 255.255.255.252
    ```
  - Kalimantan Utara
    ```bash
    auto lo
    iface lo inet loopback

    #A8 > KALIMANTAN
    auto eth0
    iface eth0 inet static
      address 10.77.21.190
      netmask 255.255.255.252
      gateway 10.77.21.189

    #A9 > SW-TANJUNG-SELOR
    auto eth1
    iface eth1 inet static
      address 10.77.18.1
      netmask 255.255.255.0

    #A10 > KALIMANTAN-TIMUR
    auto eth2
    iface eth2 inet static
      address 10.77.21.193
      netmask 255.255.255.252
    ```
  - Kalimantan Selatan
    ```bash

    ```
  - Kalimantan Timur
    ```bash

    ```
  - Lampung
    ```bash
    auto lo
    iface lo inet loopback

    #A20 > SUMATERA
    auto eth0
    iface eth0 inet static
      address 10.77.21.206
      netmask 255.255.255.252
      gateway 10.77.21.205

    #A21 > SW-BANDAR-LAMPUNG
    auto eth1   
    iface eth1 inet static
      address 10.77.19.1
      netmask 255.255.255.0   
    ```
  - Aceh
    ```bash
    auto lo
    iface lo inet loopback

    #A17 > SUMATERA-UTARA
    auto eth0
    iface eth0 inet static
      address 10.77.21.202
      netmask 255.255.255.252
      gateway 10.77.21.201

    #A18 > SW-BLANGKARAI
    auto eth1
    iface eth1 inet static
      address 10.77.20.1
      netmask 255.255.255.128

    #A19 > SW-BANDA-ACEH
    auto eth2
    iface eth1 inet static
      address 10.77.21.129
      netmask 255.255.255.224
    ```
  - Maluku Utara
    ```bash
    
    ```
  - Belawa
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
    #KE MALUKU-UTARA
    route add -net 10.77.8.0 netmask 255.255.248.0 gw 10.77.20.132

    #KE MAKASAR
    route add -net 10.77.21.160 netmask 255.255.255.248 gw 10.77.21.170

    #KE BELAWA
    route add -net 10.77.21.0 netmask 255.255.255.192 gw 10.77.21.171
    ```
  - Sumatera
    ```bash
    #KE SUMATERA-UTARA
    route add -net 10.77.21.184 netmask 255.255.255.252 gw 10.77.21.73
    route add -net 10.77.20.0 netmask 255.255.255.128 gw 10.77.21.73
    route add -net 10.77.21.128 netmask 255.255.255.224 gw 10.77.21.73

    #KE LAMPUNG
    route add -net 10.69.77.0 netmask 255.255.255.0 gw 10.77.21.206
    ```
  - Sumatera-utara
    ```bash
    route add -net 10.77.20.0 netmask 255.255.255.128 gw 10.77.21.202 #SW-BLANGKARAI
    route add -net 10.77.21.128 netmask 255.255.255.224 gw 10.77.21.202 #SW-BANDA-ACEH
    ```
  - Kalimantan
    ```bash
    route add -net 10.77.21.192 netmask 255.255.255.252 gw 10.77.21.190
    route add -net 10.77.18.0 netmask 255.255.254.0 gw 10.77.21.190
    route add -net 10.77.21.196 netmask 255.255.255.252 gw 10.77.21.190
    route add -net 10.77.21.96 netmask 255.255.255.224 gw 10.77.21.190
    route add -net 10.77.0.0 netmask 255.255.248.0 gw 10.77.21.190
    ```
  - Kalimantan Utara
    ```bash
    route add -net 10.77.16.0 netmask 255.255.254.0 gw 10.77.21.194
    route add -net 10.77.21.200 netmask 255.255.255.252 gw 10.77.21.194
    route add -net 10.77.21.96 netmask 255.255.255.224 gw 10.77.21.194
    route add -net 10.77.0.0 netmask 255.255.248.0 gw 10.77.21.194
    ```
  - Kalimantan Selatan
    ```bash
    route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.77.21.197
    ```
  - Kalimantan Timur
    ```bash
    route add -net 10.77.21.96 netmask 255.255.255.224 gw 10.77.21.198
    route add -net 10.77.0.0 netmask 255.255.248.0 gw 10.77.21.198
    ```

# CIDR


## Penggabungan - CIDR

Berikut adalah hasil dari penggabungan node: 

![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/78f7e007-4abc-43cd-a281-f26539cce9ff)
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/9d702c1c-f55e-4a15-97df-454101717ccb)

## Tree

Berikut merupakan hasil pemecahan subnet besar yang akan dibentuk menjadi jaringan yang lebih kecil

![CIDR IP TREE-3](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/3f71be82-7932-407b-92cb-23e5f80aaedc)

## Pembagian IP - CIDR

![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/f37b8d74-f56f-41d4-a959-4404465bb77c)

## Subnetting
### I1 (Netmask Terbesar)<br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/394ff90d-0d04-48b9-a118-de2b53269652)<br>
### H1<br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/fbf192c8-92b8-4d0c-a345-b11f99b0363c)<br>
### H2<br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/3a3698e1-cddf-4526-bf16-07f1a633f1fa)<br>
### G1<br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/056b17a3-0c54-4092-8e3a-beb15db3f277)<br>
### G2<br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/c5a6c318-aecf-4c39-a897-a2792835ca20)<br>
### F1<br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/0f3cc18a-a96f-430f-99e8-05aa00bb8bdb)<br>
### F2<br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/e247bec5-ada2-4e1d-8282-00e1d6b2cfa7)<br>
### F3<br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/ee435dd3-ca0f-4189-b461-05d5988b5d60)<br>
### E1<br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/40db75e8-d37e-46f5-b12a-609f398b7e3f)<br>
### E2<br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/427f0751-0d78-4db2-9c10-5d1ee3e1d2bb)<br>
### E3<br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/fe7a4bf0-ac0d-438c-873b-722c9e0415cc)<br>
### D1<br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/caad8d04-784a-4d01-8c99-13d62b4ef6e6)<br>
### D2<br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/05342995-191b-4565-ba52-80221023b9fa)<br>
### D3<br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/13830462-22d9-49f8-872e-e772d1004b60)<br>
### C1<br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/2464f82f-c83a-4c50-a8e0-13f297254853)<br>
### C2<br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/9599e694-a59e-48fb-9a38-ec34bd8164ce)<br>
### C3<br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/3c135fdb-c084-4548-89b6-6941866a9dfe)<br>
### B1<br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/0f9c99e3-b68b-49e4-9752-b25fc5c58e6a)<br>
### B2<br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/dc07a323-c888-4ffa-92a9-b7554ffadcf4)<br>
### B3<br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/0cf3a546-c6d5-44a2-8bbc-b0ad792eb0d8)<br>

### 
 - Subnetting pada CPT dilakukan pada device router dengan perintah
    ```bash
    interface <Nama interface>
    ip address <IP address> <Netmask>
    no shutdown
    ```
**JAWA** <br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/a0937240-df71-4da4-ad4c-9dd94e1d0e33) <br>
**SUMATRA** <br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/197c3d79-da3f-4f85-8766-367bc8402580) <br>
**SUMATRA UTARA** <br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/08867246-cf3d-4a51-a5ef-35eaf7412f48) <br>
**ACEH** <br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/45923adc-13d8-4c87-911a-5f939fccabb1) <br>
**LAMPUNG** <br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/661af4db-f2ca-4f68-99c5-ba5715403aa2) <br>
**KALIMANTAN** <br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/d92ba46f-f229-4f8a-b2d6-7b457530fc74) <br>
**KALIMANTAN UTARA** <br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/20fb1fb1-d43c-4471-b12e-f64ee696a4d1) <br>
**KALIMANTAN TIMUR** <br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/9cb2e11d-2b3a-4c18-aabb-192118c6080e) <br>
**KALIMANTAN SELATAN** <br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/fab48c82-9bdc-448b-a39c-57484ed12609) <br>
**SULAWESI** <br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/84f0ab45-0cf1-4ba7-aaa2-4fd61c84684e) <br>
**MALUKU UTARA** <br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/123cbca6-6134-4498-904b-64c6bde6c165) <br>
**MAKASSAR** <br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/d3b2d85d-ed67-4d75-9ac0-e5700e670761) <br>
**BELAWA** <br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/62f880a9-3a82-4478-827e-072054c26b14) <br>

- Untuk melakukan pengecekan dapat menggunakan command line `do show ip interface brief`
- Jangan lupa atur IP pada client dengan cara :
    - Masuk ke client    
    - Pilih tab Desktop
    - Pilih IP Configuration
- Keterangan:
    - IPv4 Address = pilih ip yang masih tersedia alias belum digunakan pada subnet tersebut
    - Gateaway = IP router dengan interface yang mengarah ke subnet tersebut

![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/a55c10e3-9a0f-4f8b-83bc-85a3aae3138d)

## Routing
- Routing pada CPT dilakukan pada device router dengan perintah:
    ```bash
    ip route <Destination network ID> <Netmask> <Gateway>
    ```
**Routing dari Jawa ke Subnet A4** <br>
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/29eb3ec0-7e63-4441-b0ed-fda8657d6c67)
<br>
## Testing
**Router ke Router**
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/185bab3c-e325-4306-864b-cd928b29e903)
**Router ke Client**
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/a87be7dc-607e-43a9-8fc4-1072de3ed7f3)
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/37513435-f0fe-4ccd-9882-7ebda5729bbd)
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/6f2414ce-bbd1-4b0b-8a62-16963456dd07)
**Client ke Router**
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/779c919e-de1a-41bd-bc69-3515b738508a)
**Client ke Client**
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/9ebafcc8-99c8-49c4-a4bb-7fdc5d532301)
![image](https://github.com/Zaar97/Jarkom-Modul-4-IT27-2024/assets/136430870/6d5089cc-91f1-41a9-9313-a218bc7d8676)

