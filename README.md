# minion-efk

A simple EFK (Elasticsearch, Fluentbit, Kibana) logging stack for capturing and visualizing logs from an nginx web server using Docker Compose.

## Overview

This project provides a ready-to-run logging stack for local development or small VM environments. It uses:
- **nginx**: A basic web server with access logging enabled.
- **Fluentbit**: Collects nginx logs and forwards them to Elasticsearch.
- **Elasticsearch**: Stores logs for search and analysis.
- **Kibana**: Visualizes logs from Elasticsearch.

## Prerequisites

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Quick Start

1. Clone this repository:
    ```sh
    git clone https://github.com/yourusername/minion-efk.git
    cd minion-efk
    ```

2. Prepare the nginx log directory:
    ```sh
    mkdir -p nginx-logs
    sudo chown 1000:1000 nginx-logs   # Ensure nginx can write logs
    sudo chmod 777 nginx-logs
    ```

3. Start all services:
    ```sh
    sudo docker-compose up -d
    ```

4. Access the services:
    - **nginx**: [http://localhost:8080](http://localhost:8080)
    - **Kibana**: [http://localhost:5601](http://localhost:5601)
    - **Elasticsearch**: [http://localhost:9200](http://localhost:9200)

5. View logs in Kibana:
    - Open Kibana in your browser.
    - Configure an index pattern for `nginx-logs` to visualize nginx access logs.

## File Structure

- `docker-compose.yml`: Defines all services and their relationships.
- `nginx.conf`: Minimal nginx configuration with access logging.
- `fluent-bit.conf`: Fluentbit configuration to tail nginx logs and send them to Elasticsearch.
- `nginx-logs/`: Directory where nginx writes its access logs (created at runtime).

## Stopping and Cleaning Up

To stop all services:
```sh
sudo docker-compose down
```
