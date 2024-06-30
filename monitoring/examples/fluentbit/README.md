# FluentBit

This repository provides a basic example of how to configure FluentBit to send metrics to the Ionos Monitoring Service.

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
2. Install `Fluent Bit` package, appropriate for your distribution.
3. Update the HTTP endpoint and the APIKEY in the fluentbit.conf file.
4. Configure Fluent Bit to your desired state.
5. Run fluentBit and Profit.
