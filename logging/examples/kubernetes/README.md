# Kubernetes
This a ready-make kubernetes demo of using IONOS Logging Service for your kubernetes pods logs. It uses official FluentBit container and provided config example to redirect logs from kubernetes containers using official fluentd image.

## Provision a Pipeline
Provision a Pipeline using REST API (https://logging.de-txl.ionos.com/pipelines) with source: kubernetes

### Example API Request Body
```json
{
  "properties": {
    "name": "kubernetes tcp",
    "logs": [
      {
        "source": "kubernetes",
        "tag": "k8s",
        "protocol": "tcp",
        "labels": [
          "k8slabel1", "k8slabel2"
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
2. Put provided tcp input endpoint, token and the tag into fluent-bit-configmap.yml file
3. Create a new namespace: `kubectl create namespace logging`
4. Create kubernetes objects `kubectl apply -f kubernetes`
