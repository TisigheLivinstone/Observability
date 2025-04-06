### **Overview**  
The monitoring stack comprises four main services: **Node Exporter**, **cAdvisor**, **Prometheus**, and **Grafana**. These services work together to collect, store, and visualize metrics from both the host system and running containers.  

- **Node Exporter (ne):**  
  - Collects system-level metrics from the host machine (EC2 instance).  
  - Monitors CPU, memory, disk, and network usage.  
  - Deployed separately for various environments (`sbx-ne`, `dev-ne`, `stg-ne`, `prd-ne`, `com-ne`, `crit-ne`).  

- **cAdvisor (Container Advisor):**  
  - Collects container-level metrics from Docker containers.  
  - Monitors resource usage per container, including CPU, memory, and network statistics.  
  - Deployed separately for various environments (`sbx-cadvisor`, `dev-cadvisor`, `stg-cadvisor`, `prd-cadvisor`, `com-cadvisor`, `crit-cadvisor`).  

- **Prometheus:**  
  - Scrapes metrics from **Node Exporter** and **cAdvisor** at regular intervals.  
  - Stores scraped data in a time-series database.  
  - Provides an interface for querying metrics using PromQL.  
  - Configured with dedicated jobs for different environments for both Node Exporters and cAdvisor.  

- **Grafana:**  
  - Visualizes collected metrics from Prometheus.  
  - Provides interactive dashboards and graphs for monitoring system health and performance.  
  - Allows filtering metrics by environment (jobs).  

