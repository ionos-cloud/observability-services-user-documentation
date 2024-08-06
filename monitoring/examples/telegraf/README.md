# Telegraf (InfluxData) 

Telegraf is a plugin-driven server agent for collecting and reporting metrics. Telegraf has plugins or integrations to source a variety of metrics directly from the system it’s running on, to pull in metrics from third-party APIs, or even to listen for metrics via a StatsD and Kafka consumer services. It also has output plugins to send metrics to a variety of other datastores, services, and message queues, including InfluxDB, Graphite, OpenTSDB, Datadog, Librato, Kafka, MQTT, NSQ, and many others.

## Provision a Pipeline
Provision a monitoring pipeline using REST API (https://monitoring.de-txl.ionos.com/pipelines)

### Example API Request Body
```json
{
  "properties": {
    "name": "example"
  }
}
```

## Usage:
1. Grab the key from the above response or provision a new key using REST API (https://monitoring.de-txl.ionos.com/pipelines/<PIPELINE_ID>/key).

2. Update the HTTP endpoint and the APIKEY in the prometheus config file.

- https://docs.influxdata.com/telegraf/v1/data_formats/input/prometheus-remote-write/
- https://github.com/influxdata/telegraf/blob/master/plugins/serializers/prometheusremotewrite/README.md

```toml
[[outputs.prometheus_remote_write]]
  ## URL for the prometheus remote write endpoint
  url = "https:<HTTP_ENDPOINT>/api/v1/push" 

  ## Custom HTTP Headers
  [outputs.prometheus_remote_write.headers]
    APIKEY = "<APIKEY>" 
```

