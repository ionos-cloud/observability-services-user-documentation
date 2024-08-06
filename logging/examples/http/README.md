# HTTP JSON
You can send logs through HTTP(S) connection as long as your system is able to send data as JSON.

## Provision a Pipeline
Provision a Pipeline using REST API (https://logging.de-txl.ionos.com/pipelines) with source: generic

### Example API Request Body
```json
{
  "properties": {
    "name": "http example",
    "logs": [
      {
        "source": "generic",
        "tag": "myhttp",
        "protocol": "http",
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
2. Also grab the `httpAddress` from RESP API when the pipeline is ready.
3. Send an example log ingestion as below (`myhttp` is the tag is created with the request above):

```bash
curl -X "POST" "<HTTP-ADDRESS>/myhttp" \
     -H 'Content-Type: application/json' \
     -H 'APIKEY: <KEY>' \
     -d $'{
  "status": "Notready",
  "ts": 1580306777.04728,
  "pod": {
    "name": "coredns",
    "namespace": "kube-system"
  },
  "msg": "Pod status updated",
  "level": "error",
  "label_1": "new_again_2"
}'

```
