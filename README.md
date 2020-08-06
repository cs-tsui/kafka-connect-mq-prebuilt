## Introduction
This repo's main purpose is to document the usage of a prebuilt Kafka Connect Image that includes MQ source and sink connectors.

## Deploying to Openshift
```
# Create necesary secrets
TODO

# Create deployment/routes
oc apply -f kafkaconnect-deploy.yaml
```


## Prebuilt Image Here

https://hub.docker.com/r/cstsui/kafkaconnect-mq