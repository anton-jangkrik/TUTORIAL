# Konfigurasi Network di Ubuntu 24.04
1. edit file ini
```
sudo nano /etc/netplan/50-cloud-init.yaml 
```
masukkan kode ini dan ganti IP sesuai 
``` yml
network:
    ethernets:
        ens18:
            addresses:
            - 172.16.7.50/16
            nameservers:
                addresses:
                - 172.16.7.254
                search: []
            routes:
            -   to: default
                via: 172.16.7.254
    version: 2

version: 2
network:
    ethernets:
        ens18:
            addresses:
            - 172.16.7.50/16
            nameservers:
                addresses:
                - 172.16.7.254
                search: []
            routes:
            -   to: default
                via: 172.16.7.254
```


# Konfigurasi hak akses user group
1. Tambahkan Pengguna ke Grup ```docker```
```
sudo usermod -aG docker $USER
```
Setelah menjalankan perintah ini:
```
newgrp docker
```
2. Verifikasi Keanggotaan Grup
```
groups
```
Output harus menampilkan docker dalam daftar grup.
ini berlaku juga untuk user yang lain, tinggal gantu user docker ke user yang di inginkan dalam server