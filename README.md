# NagiosToHomeAssistant
Copy of configuration and Instructions to get Nagios notifications into Home Assistant... with some Node-Red goodness as well

Needed Items:
* Working Home Assistant Instance with MQTT Broker installed and Node-Red
* Working Nagios Instance 

## Setup Nagios for MQTT ##

#### Install Stuff ####
``` sudo apt update && sudo apt install mosquitto mosquitto-clients ```

#### Check Installation and connection to MQTT Broker ####

``` mosquitto_pub -h [IP Address of MQTT Broker] -m "Test Message" -t Nagios-Alert/Test ```

#### Configure Stuff ####

* edit the /etc/nagios4/resources.cfg file and add the Items mentioned in file Nagios/resources.cfg
* edit the /etc/nagios4/objects/commands.cfg file and add the Items mentioned in file Nagios/commands.cfg
* Restart nagios

#### Test The Configuration ####
* In Home Assistant for to Integrations and the MQTT Broker Configuration, setup a listener for the topic "Nagios-Alert/#" (note /# are important) and you should see the MQTT published messages and Topic when they are sent
* Go into the Nagios UI and send "custom notification" for both a Host and Service

## Do Node-Red ##

In Node-Red import the flow from /Node-Red/NagiosAlertsFlow.json change the notification to your chosen notification mechanism bear in mind this will affect the "Data" element. In the example Flow I have my iOS device
