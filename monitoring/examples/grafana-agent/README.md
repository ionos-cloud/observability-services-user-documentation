# Grafana Agent

This example shows how to configure Grafana Agent to send metrics to the monitoring pipeline.

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

2. Install `Grafana Agent` package, appropriate for your distribution. (https://grafana.com/docs/agent/latest/about/)

3. Update the HTTP endpoint and the APIKEY in the config file.

https://grafana.com/docs/agent/latest/flow/reference/components/prometheus.remote_write/

```river
  prometheus.remote_write "LABEL" {
    endpoint {
      url = "https:<HTTP_ENDPOINT>/api/v1/push"

      headers = {
        "APIKEY" = "<API_KEY>",
      }
  }
}
```
