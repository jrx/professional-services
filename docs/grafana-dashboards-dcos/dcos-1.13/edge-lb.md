```json
{
  "id": "/prom/haproxy-exporter",
  "instances": 1,
  "portDefinitions": [
    {
      "name": "prometheus",
      "protocol": "tcp",
      "port": 0,
      "labels": {"DCOS_METRICS_FORMAT": "prometheus"}
    }
  ],
  "container": {
    "type": "MESOS",
    "volumes": [],
    "docker": {
      "image": "prom/haproxy-exporter:v0.10.0"
    }
  },
  "cpus": 0.2,
  "mem": 256,
  "requirePorts": false,
  "networks": [],
  "healthChecks": [],
  "fetch": [],
  "constraints": [],
  "env": {
    "HAPROXY_URI": "http://edgelb-pool-0-server.dcos-edgelbpoolskubectl-proxy.autoip.dcos.thisdcos.directory:6090/haproxy?stats;csv"
  },
  "cmd": "/bin/haproxy_exporter --web.listen-address=:$PORT0 --haproxy.scrape-uri=$HAPROXY_URI"
}
```