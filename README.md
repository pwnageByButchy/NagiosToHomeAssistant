# NagiosToHomeAssistant
Copy of configuration and Instructions to get Nagios notifications into Home Assistant... with some Node-Red goodness as well

Needed Items:
* Working Home Assistant Instance with MQTT Broker installed and Node-Red
* Working Nagios Instance 

### Setup Nagios for MQTT ###
``` sudo apt update && sudo apt install mosquitto mosquitto-clients ```

Check Installation and connection to MQTT Broker
``` mosquitto_pub -h [IP Address of MQTT Broker] -m "Test Message" -t Nagios-Alert/Test ```
