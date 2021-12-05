# Esp-32-Limnigraph-with-wireless-comunication-LoRa-
In this project we will desing a code for the Esp-32 using arduino IDE to read the temperature and the level of a river with a Ultrasonic sensor (jsn-sr04t-2.0) and a temperature sensor (Ds18b20) . The data will be sended from one location to another using LoRa and a master-slave comunication, then with wi-fi it will be uploaded to Adafruit.io
there are 4 codes, 2 with sleep mode and 2 witouth sleep mode. Because this is a solution for different problems and ways to create a radiolink.

WITHOUT SLEEP MODE

these pair of codes were created as a solution to a send-request from the gateway (master) to the secondary nodes (slaves) so, the order of the comunications will be defined by the master
so, we have a comunication like this example,  the gateway says node 1 send me the information, so the node 1 answers there is the information, finally the gateway publish the information to adafruit
then the gateway says node 2 send me the information...... and continue with the 3 nodes, with this we can avoid radiolink collisions, this is important because LoRa does not have multichannels-options.
LoRa just have one channel, LoRaWan has multichanel-options but is more expensive than LoRa.

PROBLEMS WITHOUT SLEEP MODE

The circuit of the TTGO-Esp32 does not allows to sleep the microcontroller using wireless comunication, you have to use timers or use touchsensors to control the sleep mode or the wake up.
So you can not put into sleep mode the secondary nodes from the master node.


WITH SLEEP MODE

in the other hand we have these pair of codes that have sleep mode on the secondary nodes, now the comunication depends on the secondary nodes, because they have the slee-wakeup option using timmers
So, to create a radiolink, the nodes just wake up and send the information to the gateway (master), the master is listening all the time.

PROBLEMS WITH SLEEP MODE

There is a low posibility to have a radiolink collision, because there is not a code to synchronize the 3 secondary nodes. this is because there isn't a way to control the sleep mode.
if you want to control the sleep mode you have to use timers.


NOTES: this is a part of a proyect called "Implementacion de modulos con comunicacion inalambrica para los limnigrafos instalados en san jose de chiquitos", so the objective is to create a radiolink
to send the information to one place to other where you can use another technology to upload the information to the internet.
