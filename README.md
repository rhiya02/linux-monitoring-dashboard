📊 Real-Time Server & Application Monitoring Using Netdata + Prometheus + Grafana

This project provides a complete monitoring solution for Linux system performance, built using:

- Netdata → System metrics exporter
- Prometheus → Metrics scraping & time-series database
- Grafana → Beautiful visualization dashboard

The dashboard includes:

CPU Usage
- Memory Usage (Total, Free, Used)
- Disk I/O
- Network Traffic
- Processes Running
- System Uptime
- Exported full Grafana JSON
This project helps beginners learn monitoring, observability, metrics collection, dashboarding, and DevOps tools.

🚀 Features
✔ Real-time monitoring
✔ Custom Grafana dashboard
✔ Prometheus scraping Netdata metrics
✔ PromQL queries included
✔ Easy setup for any Linux machine
✔ Fully open-source and customizable

📁 Project Structure
.
├── prometheus.yml              # Prometheus scrape configuration
├── grafana-dashboard.json      # Exported Grafana dashboard
├── README.md                   # Documentation

🔧 1. Install Netdata
Netdata collects all system metrics.
`bash <(curl -SsL https://my-netdata.io/kickstart.sh)...` <br>
Verify Netdata: `http://localhost:19999`

📥 2. Install Prometheus

Download:
`wget https://github.com/prometheus/prometheus/releases/download/v2.52.0/prometheus-2.52.0.linux-amd64.tar.gz
tar -xvf prometheus-2.52.0.linux-amd64.tar.gz`
Replace the default config with the included:
`cd prometheus-2.52.0.linux-amd64`
Start Prometheus: `./prometheus --config.file=prometheus.yml`
Open: `http://localhost:9090`

📡 3. Prometheus Scrape Configuration

prometheus.yml <br>
`scrape_configs:`
  `- job_name: 'netdata'
    metrics_path: '/api/v1/allmetrics'
    static_configs:
      - targets: ['localhost:19999']`

📊 4. Install Grafana

`sudo apt-get install -y adduser libfontconfig1
wget https://dl.grafana.com/oss/release/grafana_10.2.0_amd64.deb
sudo dpkg -i grafana_10.2.0_amd64.deb`
Start Grafana:
`sudo systemctl start grafana-server
sudo systemctl enable grafana-server`
Open Grafana:
`http://localhost:3000`
Default login:
`admin / admin`

📥 5. Add Prometheus as a Datasource in Grafana

1. Go to Configuration → Data Sources
2. Choose Prometheus
3. Set URL: `http://localhost:9090`
4. Save & Test

📌 6. PromQL Queries Used

CPU Usage %
`netdata_system_cpu_percentage_average`

Memory Total
`netdata_system_ram_MiB_average{dimension="total"}`

Memory Free
`netdata_system_ram_MiB_average{dimension="free"}`

Memory Used
`netdata_system_ram_MiB_average{dimension="used"}`

Network Receive & Transmit
`netdata_system_net_kilobits_persec_average{dimension="received"}
netdata_system_net_kilobits_persec_average{dimension="sent"}`

Disk I/O
`netdata_system_io_KiB_persec_average`

Processes Running
`netdata_system_processes_processes_average{dimension="running"}`

System Uptime
`netdata_system_uptime_seconds_average`

📷 7. Dashboard Preview
<img width="959" height="412" alt="grafana-dashboard" src="https://github.com/user-attachments/assets/a72352e9-4698-4c9e-9ada-d9796fb51208" />

🤝 Contributions

Feel free to open issues or pull requests.

📜 License

This project is open-source under the MIT License.

