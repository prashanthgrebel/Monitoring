# Monitoring
# Prometheus and Grafana

# Create persistent volume for your data
```
docker volume create prometheus-data
```
# Start Prometheus container
```
docker run \
    -p 9090:9090 \
    -v /path/to/prometheus.yml:/etc/prometheus/prometheus.yml \
    -v prometheus-data:/prometheus \
    prom/prometheus
```
# OR
```
version: '3'
volumes:
  prometheus_data:
services:
  prometheus:
    image: prom/prometheus
    container_name: prometheus
    volumes:
      - ./prometheus/:/etc/prometheus/
      - prometheus_data:/prometheus
    ports:
      - "9091:9090"
    command:
      - '--config.file=/etc/prometheus/prometheus.yml'
        #- '--storage.agent.path=/prometheus'
        #- '--web.console.libraries=/etc/prometheus/console_libraries'
        #- '--web.console.templates=/etc/prometheus/consoles'
        #- '--web.enable-lifecycle'
        #- '--enable-feature=agent'

```
![image](https://github.com/prashanthgrebel/Monitoring/assets/92351464/07e2ed58-3787-4b9a-89c7-9bfbce25395b)

