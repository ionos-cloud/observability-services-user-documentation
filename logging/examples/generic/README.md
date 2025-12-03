# Generic
Technically, you can send logs from anywhere as long as:
- The source has [FluentBit](https://docs.fluentbit.io/manual) installed (if you use TCP).
- The source is able to access internet.

## Provision a Pipeline
Provision a Pipeline using REST API (https://logging.de-txl.ionos.com/pipelines) with source: generic

### Example API Request Body
```json
{
  "properties": {
    "name": "generic example",
    "logs": [
      {
        "source": "generic",
        "tag": "customtcp",
        "protocol": "tcp",
        "labels": [
          "genlabel1", "genlabel2"
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
1. Grab the key from the above response or provision a new key using REST API (https://logging.de-txl.ionos.com/pipelines/<PIPELINE_ID>/key).
2. Put provided tcp input endpoint, token and the tag into fluentbit.conf file.
3. Install `Fluent Bit` package, appropriate for your distribution.
4. Configure Fluent Bit to use source you want.
5. Profit.
