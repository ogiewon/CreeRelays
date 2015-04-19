## CreeRelays
SmartThings + Cree Connected LED Bulb Zigbee board  + Arduino Nano = Cheap Home Automation Potential!

![screenshot](https://cloud.githubusercontent.com/assets/5206084/7218055/286858f2-e625-11e4-9c2b-8b85c7f28f00.PNG)

Please note that this project results in a device that is essentially a one way device.  SmartThings sends commands to the Arduino via a scavenged Cree Connected LED bulb's Zigbee board.  There is no way for the Zigbee board to send updates to SmartThings, unless a REFRESH command is sent from ST.  The Arduino has no way to tell the Zigbee board the status of anything!  The Zigbee board is capable of sending two signals to the Arduino:
- An On/Off signal (i.e. bulb on or off)
- A PWM Signal (i.e. bulb dim level)

The Cree bulb can be bought at Home Depot for about $15.  The Arduino Nano clone that I used was bought on ebay for less than $5 (and a few weeks shipping time!)

## Overview
CreeRelays consists of two parts:
- The CreeRelays.ino Arduino sketch
- The CreeRelays.device.groovy SmarThings Device Type


## Hardware Requirements
CreeRelays requires:
- Arduino Nano, UNO, or similar ($5 and up)
- Cree Connected LED Bulb's Zigbee Communication Board ($15)

## Hardware Setup Instructions
- Join your Cree Connected Bulb to your hub using your phone's SmartThings App BEFORE disassembling the bulb!!!
- After removing the Zigbee board from the Cree Connected bulb, attach it to the Arduino as follows
  - Zigbee Board Pin 1 to Arduino GND
  - Zigbee Board Pin 2 to Arduino 3.3V
  - Zigbee Board Pin 3 to Arduino Pin 11 (PWM)
  - Zigbee Board Pin 3 to Arduino Pin 12 (On/Off)
  - Arduino Pin 2 to Relay #1 (or an LED as I did for testing!)
  - Arduino Pin 3 to Relay #2 
  - Arduino Pin 4 to Relay #3 
  - Arduino Pin 5 to Relay #4
  - Arduino Pin 6 to Relay #5
  - Arduino Pin 7 to Relay #6
  - Arduino Pin 8 to Relay #7
  - Arduino Pin 9 to Relay #8

![screenshot](https://cloud.githubusercontent.com/assets/5206084/7218058/35927de6-e625-11e4-8915-0ff51ccc8f30.JPG)
![screenshot](https://cloud.githubusercontent.com/assets/5206084/7218060/3bc030aa-e625-11e4-81d7-e59e2e75df42.JPG)


##CreeRelays Arduino Setup Instructions
- Join your Cree Connected Bulb to your hub using your phone's SmartThings App BEFORE disassembling the bulb!!!
- Download the CreeRelays repository.
- This folder structure should mirror that of your local Arduino directory. 
  - On Mac, it's located in `~/Documents/Arduino/`.
  - On Windows, it's located in `C:\My Documents\Arduino`.
- Look inside the `Arduino/Sketches` folder of the repo.
- Copy and paste the `CreeRelays` sketch folder into your local Arduino sketches directory. If you haven't created any sketches, you may not see the folder. In this case, feel free to create it.


##CreeRelays SmartThings Device Type Installation Instructions
- Join your Cree Connected Bulb to your hub using your phone's SmartThings App BEFORE disassembling the bulb!!!
- Create an account and/or log into the SmartThings Developers Web IDE.
- Click on My Device Types from the navigation menu.
- Click on  + New SmartDevice button.
- Fill in the Name field as CreeRelays and click on the Create button. Don't worry about filling out everything else.
- Paste the code from the CreeRelays.device.groovy file from this repo.
- Click on  Save  in the IDE.
- Click on  Publish -> For Me  in the IDE.
- Click on My Devices from navigation menu
- Select your "Arduino ThingShield" device from the list
- Click the Edit button at the bottom of the screen
- Change the Type to "CreeRelays"
- Click the Update button at the bottom of the screen
- On your phone, log out of SmartThings in the app, and then log back into SmartThings to refresh its settings
- Your CreeRelays Device Tile should now look like the image above in this ReadMe

##CreeRelays Usage
- This is essentially a proof of concept example.  You can control up to 8 relays with this example as-is.  My intention was to share this project as an inspiration for others to kick-start any other efforts that desire a very low cost way to control real-world devices from SmartThings.
- Pressing any of the "Relay 1" through "Relay 8" tiles on your phone will "turn on the bulb and set the dim level to 1 through 8 respectively."
- Based on the dim level selected, the arduino sketch will turn on a corresponding digital output (which could be conncted to a relay.)
- Pressing a different "Relay n" tile will turn off the previous output, and turn on the new output
- Pressing the main "Lightbulb" tile will either turn on or turn off the output which corresponds to the current Dim Level
- Only Dim Levels 1 through 8 are currently being handled by the Arduino sketch.  Using the slider control to set dim levels above 8 or below 1 will turn off all of the output pins.  Note: All 100 dim levels are properly recognized in the Arduino Sketch, but I only have code in place for values 1 though 8 in this example.
- Only one digital output can be on at a time in the current example.  For more complicated designs, the exercise is left up to the student!




