Start service:
```
sudo docker-compose up -d
```
Prometheus is available at [http://127.0.0.1:9090](http://127.0.0.1:9090). Here PromQL queries can be executed. 
Active exporters: [http://127.0.0.1:9090/targets](http://127.0.0.1:9090/targets)
BlackBox exporter: [http://127.0.0.1:9115](http://127.0.0.1:9115)
All metrix provided by BlackBox exporter: [http://127.0.0.1:9115/metrics](http://127.0.0.1:9115/metrics)

To get Grafana container work properly create a ./grafana/provisioning/ directory and change its ownership to `grafana` user as follows:
```
sudo chown -R 472:472 grafana/
```
Otherwise Grafana container will not have writing permissions to its /var/lib/grafana directory. 
Grafana is available at [http://127.0.0.1:3000](http://127.0.0.1:3000).

When setting Prometheus as a data source for Grafana specify its URL as:
```
http://prometheus:9090
```
It is important to have `http://` and `prometheus` as a name of a target host. Otherwise connection will not be established.

To get Alertmanager working properly set onership to `alertmanager` directory and its content to a `nobody` user like this:
```
sudo chown -R nobody:nogroup ./alertmanager
```
