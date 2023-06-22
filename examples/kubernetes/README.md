# Kubernetes POC
This a ready-make kubernetes demo of using IONOS Logging Service for your kubernetes pods logs. It uses official FluentBit container and provided config example to redirect logs from kubernetes containers using official fluentd image.
## Usage:
1. Provision a Pipeline using REST API (https://logging.de-txl.ionos.com/pipelines) with source: kubernetes
2. Grab the key from the above response or provision a new key using REST API (https://logging.de-txl.ionos.com/pipelines/<PIPELINE_ID>/key)
3. Put provided tcp input endpoint, token and the tag into fluent-bit-configmap.yml file
4. Create a new namespace: `kubectl create namespace logging`
5. Create kubernetes objects `kubectl apply -f kubernetes`
