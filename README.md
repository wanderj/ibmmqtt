# ibmmqtt
This Docker image is  is an adaptation from [ibm-messaging/mq-docker](https://github.com/ibm-messaging/mq-docker) of Arthur Barr <arthur.barr@uk.ibm.com>
# Build
After extracting the code from this repository, you can build an image with the version 8 of MQ using the following command:

```
sudo docker build --tag ibm-mqtt .
```

## Running with the default configuration
You can run a queue manager with the default configuration and a listener on port 1414 using the following command.  Note that the default configuration is locked-down from a security perspective, so you will need to customize the configuration in order to effectively use the queue manager.  For example, the following command creates and starts a queue manager called `QM_MQTT`, and maps port 1414 on the host to the MQ listener on port 1414 inside the container:

```
sudo docker run \
   --env LICENSE=accept \
   --env MQ_QMGR_NAME=QM_MQTT \
   --volume /var/mqm:/var/mqm \
   --publish 1414:1414 \
   --publish 1883:1883 \
   --name ibm-mqttv8 \
   --detach \
   ibm-mqtt

```


Note that in this example, the name "ibm-mqtt" is the image tag you used in the previous build step.
