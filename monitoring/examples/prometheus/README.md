# Prometheus

Prometheus is a monitoring and alerting toolkit that is designed for reliability and scalability. 
It is a pull-based system that scrapes metrics from instrumented jobs, either directly or via an intermediary push gateway for short-lived jobs. It stores all scraped samples locally and runs rules over this data to either aggregate and record new time series from existing data or generate alerts.

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

2. Install `Prometheus` package, appropriate for your distribution.

3. Update the HTTP endpoint and the APIKEY in the prometheus config file.

https://prometheus.io/docs/prometheus/latest/configuration/configuration/#remote_write

```yaml
url: "https:<HTTP_ENDPOINT>/api/v1/push"
headers:
  APIKEY: "<APIKEY>"
```
