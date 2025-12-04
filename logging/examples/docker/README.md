# Docker
This a ready-make docker-compose demo of using IONOS Logging Service for your Docker container logs. It uses official FluentBit docker container and provided config example to redirect logs from docker containers using official docker fluentd log driver.

## Provision a Pipeline
Provision a Pipeline using REST API (https://logging.de-txl.ionos.com/pipelines) with source: docker

### Example API Request Body
```json
{
  "properties": {
    "name": "docker tcp",
    "logs": [
      {
        "source": "docker",
        "tag": "dock",
        "protocol": "tcp",
        "labels": [
          "dlabel1", "dlabel2"
        ],
         "destinations": [
          {
            "type": "loki",
            "retentionInDays": 7
          }
        ]
      }
    ]
  }
}
```

## Usage:
1. Grab the key from the above response or provision a new key using REST API (https://logging.de-txl.ionos.com/pipelines/<PIPELINE_ID>/key)
2. Put provided tcp input endpoint, token and the tag into fluentbit.conf file
3. Run docker-compose up -d
4. Observe Loki in the provided Grafana endpoint from the REST API.
5. Profit


