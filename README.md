## !! For use of the Prometheus & Grafana docker-compose stack !!
Check original repo: https://github.com/vegasbrianc/prometheus or check the PROMETHEUS_README.md in this repo.

### 1: Add HOST/PORT to trix configuration:

I have added target configuration for Trix in: https://github.com/idebruijn/prometheus/blob/master/prometheus/prometheus.yml adjust HOST and PORT

```
  - job_name: 'trix'
    metrics_path: '/actuator/prometheus'
    scrape_interval: 5s
    static_configs:
         - targets: ['HOST:PORT']

```

```
HOST: use your <Host IP Address> not localhost, because Trix in not running in the network.
PORT: port of Trix is (default 8084)
```

### 2: Start up cmd
```
HOSTNAME=$(hostname) docker stack deploy -c docker-stack.yml prom
```

### 3: Log in Grafana
Accessible via: 
```
http://<Host IP Address>:3000 for example http://192.168.10.1:3000
```

```
username - admin
password - foobar (Password is stored in the `/grafana/config.monitoring` env file)
```

### 4: Shut down cmd
docker stack rm prom

#### 5: Location JSON file
TODO
