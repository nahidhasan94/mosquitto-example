#### Docker Run:
```sh
docker run --rm -it --name mosquitto -e USERNAME=klovercloud -e PASSWORD=keepitsecret -p 1883:1883 --read-only -v /vol/mosquitto/run:/mosquitto/run -v /vol/mosquitto/data:/mosquitto/data klovercloud/mosquitto:2.0
```
####

#### Environment Variables:
- `USERNAME: <YOUR_MQTT_USERNAME>` (Default: mosquitto)
- `PASSWORD: <YOUR_MQTT_PASSWORD>` (Default: mosquitto)


####
#### Run in KloverCloud:
- Make a fork or clone of this repository to your attached git account with KloverCloud
- On-board the forked / cloned repository as an Application
- Set Application Port to `1883`
- External Access Protocol to `TCP`
- Set Health Check as `None` (For now)
- Minimum 1 GB of persistent volume is required with the following volume mount paths    
`/mosquitto/data`    
`/mosquitto/run`    
- Create Application
- Create a Secret with the given Environment Variables
- Deploy


#### Test Connection:

***With Docker***
```sh
mqtt test -h <YOUR_MOSQUITTO_EXTERNAL_ENDPOINT> -p 1883 -u <YOUR_MQTT_USERNAME> -pw <YOUR_MQTT_PASSWORD>
```

###

***With KloverCloud***
```sh
mqtt test -h <YOUR_MOSQUITTO_EXTERNAL_ENDPOINT> -p 443 --secure -u <YOUR_MQTT_USERNAME> -pw <YOUR_MQTT_PASSWORD>
```
