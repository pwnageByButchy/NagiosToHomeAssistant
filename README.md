# NagiosToHomeAssistant
So why do this after all Nagios sends notifications?

My reasons:
* Nagios already monitors all my shit... computers, interwebs, servers, services and security cameras
* Well so I can automate fixes
* All notifications for my house and my servers come through one mechanism
* Actionable Notifications
* Reducing Email Spam weird I know 
* The Power God Dam You... Unlimited Pooooooower!!!!

Essentially after the Nagios Machine has stuff installed, it is simply copy configurations... then with some Node-Red goodness for a basic notification, you're done!

Needed Items:
* Working Home Assistant Instance with MQTT Broker and Node-Red installed
* Working Nagios Instance 

## Setup Nagios for MQTT ##

#### Install Stuff ####
``` sudo apt update && sudo apt install mosquitto mosquitto-clients ```

#### Check Installation and connection to MQTT Broker ####

``` mosquitto_pub -h [IP Address of MQTT Broker] -m "Test Message" -t Nagios-Alert/Test ```

#### Configure Stuff ####

* edit the /etc/nagios4/resources.cfg file and add the Items mentioned in file /Nagios/resources.cfg
* edit the /etc/nagios4/objects/commands.cfg file and add the Items mentioned in file /Nagios/commands.cfg
* Restart nagios

#### Test The Configuration ####
* In Home Assistant go to the Integrations and the MQTT Broker Configuration, setup a listener for the topic "Nagios-Alert/#" (note /# are important) and you should see the MQTT published messages and Topic when they are sent
* Go into the Nagios UI and send "custom notification" for both a Host and a Service

## Do Node-Red ##

* In Node-Red import the flow from /Node-Red/NagiosAlertsFlow.json change the notification to your chosen notification mechanism bear in mind this will affect the "Data" element. In the example Flow I have my iOS device

## Where to Now ##
I plan to work on some automations that can then call scripts in Home Assistant to hopefully fix or investigate, minor issues with the Host or Service reporting the problem. 

Then later to create Actionable notifications for some of these to hopefully resolve common issues
