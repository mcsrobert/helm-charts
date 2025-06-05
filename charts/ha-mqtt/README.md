# ha-mqtt

This Helm chart that deploys [Home Assistant](https://www.home-assistant.io/) with [Mosquitto](https://mosquitto.org/) as [MQTT](https://mqtt.org/) server and other services that use MQTT ([Zigbee2MQTT](https://www.zigbee2mqtt.io/) and [ring-mqtt](https://github.com/tsightler/ring-mqtt)).

These are all also available as Home Assistant addons. This chart was created to allow me to migrate from that ecosystem to Kubernetes.

## Install / Upgrade

Basic usage:

```bash
helm upgrade --install hat-mqtt ha-mqtt/ha-mqtt --values my_values.yaml
```

## Configuration

To see what can be configured, see [values.yaml](./values.yaml). Also, see the [examples/](./examples/) directory.


### Passwords / Mosquitto Hash

Mosquitto expects passwords in the password file to be hashed in a certain way <sup>[1](https://mosquitto.org/man/mosquitto_passwd-1.html) [2](https://github.com/eclipse/mosquitto/blob/master/src/password_mosq.h)</sup>. As Helm does not provide the functionality to hash these passwords, you will have to hash these passwords yourself. This is [fairly easy to do with Python](https://stackoverflow.com/questions/69036942/ansible-create-sha512-pbkdf2-hash/74247083#74247083).

I personally use Ansible to fully automate installing Helm charts, just like the previously linked StackOverflow post.
