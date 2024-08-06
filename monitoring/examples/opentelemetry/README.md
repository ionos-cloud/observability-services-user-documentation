# OpenTelemetry 

OpenTelemetry is a set of APIs, libraries, agents, and instrumentation to provide observability for cloud-native software. It is a CNCF project.

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

2. Update the HTTP endpoint and the APIKEY in the config file.

https://github.com/open-telemetry/opentelemetry-collector-contrib/blob/main/exporter/prometheusremotewriteexporter/README.md

```yaml
exporters:
  prometheusremotewrite:
    endpoint: "https:<HTTP_ENDPOINT>/api/v1/push"
    external_labels:
      APIKEY: <API_KEY>
      label_name2: label_value2
```
