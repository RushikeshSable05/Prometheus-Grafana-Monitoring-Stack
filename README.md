# 📊 Prometheus + Grafana Monitoring Stack (with Node Exporter)

This repository contains a complete Docker Compose setup for running **Prometheus**, **Grafana**, and **Node Exporter** to monitor system metrics such as CPU, memory, disk usage, and more.

---

## 🚀 Features
- Prometheus for metrics scraping  
- Grafana for dashboards & visualization  
- Node Exporter to collect host system metrics  
- Easy one-command startup using Docker Compose  
- Importable Grafana dashboards (Node Exporter Full)

---

## 📁 Project Structure

.
├── docker-compose.yml
└── prometheus.yml

yaml
Copy code

---

## 🐳 Docker Compose Configuration

### `docker-compose.yml`

version: '3'
services:

  prometheus:
    image: prom/prometheus
    volumes:
      - ./prometheus.yml:/etc/prometheus/prometheus.yml
    ports:
      - "9090:9090"

  grafana:
    image: grafana/grafana
    ports:
      - "3000:3000"
    environment:
      - GF_SECURITY_ADMIN_USER=admin
      - GF_SECURITY_ADMIN_PASSWORD=admin

  node_exporter:
    image: prom/node-exporter
    ports:
      - "9100:9100"

### `prometheus.yml`

global:
  scrape_interval: 15s

scrape_configs:
  - job_name: 'prometheus'
    static_configs:
      - targets: ['prometheus:9090']

  - job_name: 'node_exporter'
    static_configs:
      - targets: ['node_exporter:9100']


▶️ Getting Started
1. Clone the repository
git clone <your-repo-url>
cd <repo-folder>

2. Start the monitoring stack
docker-compose up -d

🔍 Access Dashboards & Metrics
Prometheus UI

👉 http://localhost:9090

Grafana Dashboard

👉 http://localhost:3000

Username: admin

Password: admin

Add Prometheus as a Data Source

URL: http://prometheus:9090

📈 Import Recommended Grafana Dashboard

For full server monitoring:

Dashboard ID: 1860 (Node Exporter Full)
Available in Grafana → Import → Enter ID
