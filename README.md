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
