## langkah install prometheus di ubuntu 24.04
# Download prometheus versi terbaru
- [Download Prometheus](https://prometheus.io/download/)
```
wget https://github.com/prometheus/prometheus/releases/download/v3.2.1/prometheus-3.2.1.linux-amd64.tar.gz
```
# extrak file prometheus di server
```
tar xvf prometheus-3.2.1.linux-amd64.tar.gz prometheus-3.2.1.linux-amd64/
```
# pindah ke direktory prometheus
```
cd prometheus-3.2.1.linux-amd64
```
# Sebelum install prometheus buat user terlebih dahulu dengan nama "prometheus"
```
sudo groupadd --system prometheus
sudo useradd --system -s /sbin/nologin -g prometheus prometheus
```
# Pindahkan file prometheus dan promtool
```
sudo mv prometheus promtool /usr/local/bin/
```
# buat folder di /etc/ dan di /var/ untuk menyimpan pengaturan serta data prometheus
```
sudo mkdir /etc/prometheus
sudo mkdir /var/lib/prometheus
```
