# CreeRelays
SmartThings + Cree Connected LED Bulb Zigbee board  + Arduino Nano = Cheap Home Automation Potential

This repository contains an Arduino Sketch called "CreeRelays.ino" and a SmartThings Groovy Device Type called "CreeRelays.device.groovy".  When used together, along with ~$20 worth of hardware, one is able to control 8 relays from the SmartThings phone app.  This is just an example of what is possible.  Hopefully others will find this useful for integrating devices with SmartThings.  

Please note that this project results in a device that is essentially a one way device.  SmarTthings sends commands to the Arduino via a scavenged Cree Connected LED bulb's Zigbee board.  There is no way for the Zigbee board to send updates to SmartThings, unless a REFRESH command is sent from ST.  The Arduino has no way to tell the Zigbee board the status of anything!  The Zigbee board is capable of sending two signals to the Arduino:

-An On/Off signal (i.e. bulb on or off)

-A PWM Signal (i.e. bulb dim level)

The Cree bulb can be bought at Home Depot for about $15.  The Arduino Nano clone that I used was bought via an ebay for less than $5 (and a few weeks shipping time!)




