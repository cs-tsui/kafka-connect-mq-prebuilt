## Introduction
This repo's main purpose is to document the usage of a prebuilt Kafka Connect Image that includes MQ source and sink connectors.

## Deploying to Openshift
```
# Create connection secret
cp config/connect-distributed.properties connect-distributed.properties.orig
sed '/^#/d;/^[[:space:]]*$/d' < connect-distributed.properties.orig > connect-distributed.properties
oc create secret generic connect-distributed-config --from-file=connect-distributed.properties

# Create ConfigMap
cp config/connect-log4j.properties connect-log4j.properties.orig
sed '/^#/d;/^[[:space:]]*$/d' < connect-log4j.properties.orig > connect-log4j.properties
oc create configmap connect-log4j-config --from-file=connect-log4j.properties

# Create secret with jks file
oc create secret generic connect-jks --from-file=es-cert.jks=./es-cert.jks --type=opaque

# Create deployment/routes
oc apply -f kafkaconnect-deploy.yaml
```


## Prebuilt Image Here

https://hub.docker.com/r/cstsui/kafkaconnect-mq