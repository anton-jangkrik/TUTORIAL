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
5. Pindah ke direktory prometheus
```
cd prometheus-3.2.1.linux-amd64
```
6. Pindahkan file prometheus dan promtool
```
sudo mv prometheus.yml /etc/prometheus/
sudo mv prometheus promtool /usr/local/bin/
```
7. Rubah hak akase folder ke user prometheus
  ```
sudo chown -R prometheus:prometheus /var/lib/prometheus/
```

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
