# Docker POC
This a ready-make docker-compose demo of using IONOS Logging Service for your Docker container logs. It uses official FluentBit docker container and provided config example to redirect logs from docker containers using official docker fluentd log driver.

## Usage:
1. Provision a Pipeline using REST API (https://logging.de-txl.ionos.com/pipelines) with source: docker
2. Grab the key from the above response or provision a new key using REST API (https://logging.de-txl.ionos.com/pipelines/<PIPELINE_ID>/key)
3. Put provided tcp input endpoint, token and the tag into fluentbit.conf file
4. Run docker-compose up -d
5. Observe Loki in the provided Grafana endpoint from the REST API.
6. Profit
