# 📊 Real-Time Server & Application Monitoring Using Netdata + Prometheus + Grafana

This project provides a complete monitoring solution for Linux system performance, built using:

- Netdata → System metrics exporter
- Prometheus → Metrics scraping & time-series database
- Grafana → Beautiful visualization dashboard

The dashboard includes:

- CPU Usage
- Memory Usage (Total, Free, Used)
- Disk I/O
- Network Traffic
- Processes Running
- System Uptime
- Exported full Grafana JSON
This project helps beginners learn monitoring, observability, metrics collection, dashboarding, and DevOps tools.

## 🚀 Features
✔ Real-time monitoring <br>
✔ Custom Grafana dashboard <br>
✔ Prometheus scraping Netdata metrics<br>
✔ PromQL queries included <br>
✔ Easy setup for any Linux machine <br>
✔ Fully open-source and customizable <br>

 ## 📁 Project Structure
.<br>
├── prometheus.yml              
├── grafana-dashboard.json      
├── README.md                   

### 🔧 1. Install Netdata
Netdata collects all system metrics. <br>
`bash <(curl -SsL https://my-netdata.io/kickstart.sh)` <br>

Verify Netdata: <br>
`http://localhost:19999`

### 📥 2. Install Prometheus

Download: <br>
`wget https://github.com/prometheus/prometheus/releases/download/v2.52.0/prometheus-2.52.0.linux-amd64.tar.gz
tar -xvf prometheus-2.52.0.linux-amd64.tar.gz` <br>

Replace the default config with the included: <br>
`cd prometheus-2.52.0.linux-amd64`<br>

Start Prometheus: <br>
`./prometheus --config.file=prometheus.yml`<br>

Open:<br>
`http://localhost:9090`<br>

### 📡 3. Prometheus Scrape Configuration

prometheus.yml <br>

`scrape_configs:` <br>
  `- job_name: 'netdata'` <br>
    `metrics_path: '/api/v1/allmetrics'` <br>
    `static_configs:`<br>
     ` - targets: ['localhost:19999']`<br>

### 📊 4. Install Grafana

`sudo apt-get install -y adduser libfontconfig1
wget https://dl.grafana.com/oss/release/grafana_10.2.0_amd64.deb
sudo dpkg -i grafana_10.2.0_amd64.deb` <br>

Start Grafana: <br>
`sudo systemctl start grafana-server
sudo systemctl enable grafana-server` <br>

Open Grafana:<br>
`http://localhost:3000` <br>

Default login:<br>
`admin / admin`

### 📥 5. Add Prometheus as a Datasource in Grafana

1. Go to Configuration → Data Sources
2. Choose Prometheus
3. Set URL: `http://localhost:9090`
4. Save & Test

### 📌 6. PromQL Queries Used

**CPU Usage %:** <br>
`netdata_system_cpu_percentage_average`

**Memory Total:**<br>
`netdata_system_ram_MiB_average{dimension="total"}`

**Memory Free:**<br>
`netdata_system_ram_MiB_average{dimension="free"}`

**Memory Used:**<br>
`netdata_system_ram_MiB_average{dimension="used"}`

**Network Receive & Transmit:**<br>
`netdata_system_net_kilobits_persec_average{dimension="received"}
netdata_system_net_kilobits_persec_average{dimension="sent"}`

**Disk I/O:**<br>
`netdata_system_io_KiB_persec_average`

**Processes Running:**<br>
`netdata_system_processes_processes_average{dimension="running"}`

**System Uptime:**<br>
`netdata_system_uptime_seconds_average`

### 📷 7. Dashboard Preview
<img width="959" height="412" alt="grafana-dashboard" src="https://github.com/user-attachments/assets/a72352e9-4698-4c9e-9ada-d9796fb51208" />

## 🤝 Contributions

Feel free to open issues or pull requests.

## 📜 License

This project is open-source under the MIT License.

