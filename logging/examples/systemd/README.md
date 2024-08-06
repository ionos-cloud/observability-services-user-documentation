# Linux systemd
To use Logging Service in a Linux system with systemd journald you need to install an appropriate package for your distribution. Instructions on doing so can be found on the official [Fluent Bit Website](https://docs.fluentbit.io/manual/installation/getting-started-with-fluent-bit).

## Provision a Pipeline
Provision a Pipeline using REST API (https://logging.de-txl.ionos.com/pipelines) with source: systemd

### Example API Request Body
```json
{
  "properties": {
    "name": "systemd tcp",
    "logs": [
      {
        "source": "systemd",
        "tag": "sys",
        "protocol": "tcp",
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
3. Install `Fluent Bit` package, appropriate for your distribution.
4. Configure Fluent Bit to use source `systemd` and appropriate unit filters (example is `fluentbit.conf`). 
5. Start services you've set in `systemd unit` filters in config 
6. Profit
