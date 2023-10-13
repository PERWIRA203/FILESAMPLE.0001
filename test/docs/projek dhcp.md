# Project DHCP  

## 1. Masuk ke debian di vm ware  
## 2. Masuk sebagai root user  
## 3. Cek nama interface jaringan dengan perintah "ip a"  
## 4. Mengkonfigurasi IP di Debian.
    - Konfigurasi IP pada debian hanya dapat dilakukan menggunakan root, konfigurasi ini berada pada file /etc/network/ interfaces.  
    ```
    nano /etc/network/interfaces
    ```   
    - Mengkonfigurasi IP pada file
   Atur address IP sesuai dengan IP yang digunakan, lalu mengatur netmask IP tersebut, aturlah networknya, dan atur gateway yang digunakan untuk IP tersebut.  


   ```

    # The loopback network interface
    auto lo
    iface lo inet loopback

    # The primary network interface
    auto eth0
    iface eth0 inet static
        address 192.168.0.1
        netmask 255.255.255.224
        network 192.168.0.0
        gateway 192.168.0.1
  
## 5.Ctrl x untuk save setting IP    
## 6.Restart settingan ip tersebut dengan perintah "service networking restart"  

    
    service networking restart
    
## 7.Masukkan CD 2 Debian dari Virtual  
## 8.ketik perintah untuk menambahkan cd "apt-cdrom add" lalu enter  
```apt-cdrom add```  
## 9.Ketik perintah "apt-get update" untuk mengupdate data dari cd 2 debian tersebut  
```apt-get-update```  
## 10.Install DHCP Server dengan perintah "apt-get install isc-dhcp-server"  
```apt-get install isc-dhcp-server ```   
## 11.ketik perintah "nano /etc/dhcp/dhcpd.conf" untuk setting ip pada dhcp  
```nano /etc/dhcp/dhcpd.conf```    
## 12.Atur setting ip pada dhcp, subnet mask, gateway, dan nama network  
```

# A slightly different configuration for an internal subnet.
subnet 192.168.0.0 netmask 255.255.255.224 {
  range 192.168.0.1 192.168.0.10;
  option domain-name-servers 192.168.0.1;
  option domain-name "waduh";
  option routers 192.168.0.1;
  option broadcast-address 192.168.0.255;
  default-lease-time 600;
  max-lease-time 7200;
}




```
## 13.Ctrl x untuk save konfigurasi dhcp servernya  
## 14.Restart dhcp menggunakan perintah "service isc-dhcp-server restart"  
```service isc-dhcp-server restart```  
## 15.Sekarang kita beralih ke pc client pada virtual, misal saya menggunakan Windows 7 pada VMware  
## 16.cek setting network pada windows 7  
## 17.Jika IP windows 7 sesuai dengan settingan ip di dhcp kita maka dhcp sudah menyala.
