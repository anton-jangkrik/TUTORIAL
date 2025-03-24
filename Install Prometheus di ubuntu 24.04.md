# langkah install prometheus di ubuntu 24.04
## INSTALL PROMETHEUS
1. Download prometheus versi terbaru
- [Download Prometheus](https://prometheus.io/download/)
```
wget https://github.com/prometheus/prometheus/releases/download/v3.2.1/prometheus-3.2.1.linux-amd64.tar.gz
```
2. Extrak file prometheus di server
```
tar xvf prometheus-3.2.1.linux-amd64.tar.gz prometheus-3.2.1.linux-amd64/
```
3. Sebelum install prometheus buat user terlebih dahulu dengan nama "prometheus"
```
sudo groupadd --system prometheus
sudo useradd --system -s /sbin/nologin -g prometheus prometheus
```
4.  buat folder di /etc/ dan di /var/ untuk menyimpan pengaturan serta data prometheus
```
sudo mkdir /etc/prometheus
sudo mkdir /var/lib/prometheus
```
5. Rubah hak akase folder ke user prometheus
  ```
sudo chown -R prometheus:prometheus /var/lib/prometheus/
```
6. Pindah ke direktory prometheus
```
cd prometheus-3.2.1.linux-amd64
```
6. Pindahkan file prometheus dan promtool ke direktory ```/usr/local/bin/``` dan file prometheus.yml ke direktory ```/etc/prometheus/``` sesuai yang sudah kita buat tadi
```
sudo mv prometheus.yml /etc/prometheus/
sudo mv prometheus promtool /usr/local/bin/
```
8. agar service prometheus berjalan di belakang layar maka perlu di buatkan servicenya dan diconfigurasi
   ```
   sudo nano /etc/systemd/system/prometheus.service
   ```
   code
   ```txt
    [Unit]
    Description=Prometheus
    Wants=network-online.target
    After=network-online.target
    
    [Service]
    User=prometheus
    Group=prometheus
    ExecStart=/usr/local/bin/prometheus \
    --config.file=/etc/prometheus/prometheus.yml \
    --storage.tsdb.path=/var/lib/prometheus \
    --web.console.templates=/etc/prometheus/consoles \
    --web.console.libraries=/etc/prometheus/console_libraries
    Restart=always
    
    [Install]
    WantedBy=multi-user.target
   ```
9. reload service systemd nya
    ```
    sudo systemctl daemon-reload
    sudo systemctl status prometheus
    sudo systemctl enable --now prometheus

    ```
11. Prometheus dapat di akses langsung di alamat ip local servernya, untuk melihat brp ip servernya bisa dengan ketik ```hostname -I ``` kemudian buka di browser ip tersebut dan tambahkan port prometheus yaitu default ```9090```


## INSTALL NODE_EXPORTER
1. Download Node_Exporter versi terbaru
- [Download Node_Exporter](https://prometheus.io/download/#node_exporter)
```
wget https://github.com/prometheus/node_exporter/releases/download/v1.9.0/node_exporter-1.9.0.linux-amd64.tar.gz
```
2. Extrak file Node_Exporter di server
```
tar xvf node_exporter-1.9.0.linux-amd64.tar.gz node_exporter-1.9.0.linux-amd64/
```
