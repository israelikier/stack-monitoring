# stack-monitoring

First, create a directory to tempo and change owner permissions:

```console
mkdir tempo-data/
sudo chown 10001:10001 tempo-data/
```

To start stack monitoring:

```bash
docker-compose up -d
```

Ensure all containers are running:

```bash
docker-compose ps
```

Example:

```bash
NAME                            IMAGE                                       COMMAND                  SERVICE         CREATED          STATUS                    PORTS
alertmanager                    prom/alertmanager:v0.25.0                   "/bin/alertmanager -…"   alertmanager    4 hours ago      Up 15 minutes             0.0.0.0:9093->9093/tcp
cadvisor                        gcr.io/cadvisor/cadvisor:v0.46.0            "/usr/bin/cadvisor -…"   cadvisor        4 hours ago      Up 15 minutes (healthy)   8080/tcp
grafana                         grafana/grafana:11.0.0-preview              "/run.sh"                grafana         15 minutes ago   Up 15 minutes             0.0.0.0:3000->3000/tcp
monitoring-stack-backend-1      grafana/loki:3.0.0                          "/usr/bin/loki -conf…"   backend         4 hours ago      Up 15 minutes             0.0.0.0:65510->3100/tcp, 0.0.0.0:65511->7946/tcp
monitoring-stack-flog-1         mingrammer/flog                             "flog -f json -d 200…"   flog            4 hours ago      Up 15 minutes             
monitoring-stack-gateway-1      nginx:latest                                "sh -euc 'cat <<EOF …"   gateway         4 hours ago      Up 15 minutes (healthy)   80/tcp, 0.0.0.0:3100->3100/tcp
monitoring-stack-k6-tracing-1   ghcr.io/grafana/xk6-client-tracing:latest   "/k6-tracing run /ex…"   k6-tracing      4 hours ago      Up 16 minutes             
monitoring-stack-minio-1        minio/minio                                 "sh -euc 'mkdir -p /…"   minio           4 hours ago      Up 15 minutes (healthy)   0.0.0.0:65491->9000/tcp
monitoring-stack-read-1         grafana/loki:3.0.0                          "/usr/bin/loki -conf…"   read            4 hours ago      Up 15 minutes (healthy)   0.0.0.0:3101->3100/tcp, 0.0.0.0:65500->7946/tcp, 0.0.0.0:65501->9095/tcp
monitoring-stack-write-1        grafana/loki:3.0.0                          "/usr/bin/loki -conf…"   write           4 hours ago      Up 15 minutes (healthy)   0.0.0.0:3102->3100/tcp, 0.0.0.0:65498->7946/tcp, 0.0.0.0:65499->9095/tcp
node-exporter                   prom/node-exporter:v1.5.0                   "/bin/node_exporter …"   node-exporter   4 hours ago      Up 15 minutes             9100/tcp
prometheus                      prom/prometheus                             "/bin/prometheus --c…"   prometheus      4 hours ago      Up 15 minutes             0.0.0.0:9090->9090/tcp
redis                           redis:6                                     "docker-entrypoint.s…"   redis           4 hours ago      Up 15 minutes             0.0.0.0:6379->6379/tcp
```

To access grafana:

http://localhost:3000

