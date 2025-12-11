📊 Real-Time Server & Application Monitoring Using Netdata + Prometheus + Grafana

This project provides a complete monitoring solution for Linux system performance, built using:

Netdata → System metrics exporter

Prometheus → Metrics scraping & time-series database

Grafana → Beautiful visualization dashboard

The dashboard includes:

CPU Usage

Memory Usage (Total, Free, Used)

Disk I/O

Network Traffic

Processes Running

System Uptime

Exported full Grafana JSON

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

bash <(curl -SsL https://my-netdata.io/kickstart.sh)
Verify Netdata:

http://localhost:19999

📥 2. Install Prometheus

Download:

wget https://github.com/prometheus/prometheus/releases/download/v2.52.0/prometheus-2.52.0.linux-amd64.tar.gz
tar -xvf prometheus-2.52.0.linux-amd64.tar.gz
cd prometheus-2.52.0.linux-amd64
