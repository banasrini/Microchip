
### Introduction

At PubNub, we are always trying to integrate our realtime software with new hardware, and this time it is with Microchip Technology. The number of platforms we support only keep increasing everyday, and we are super excited to announce this latest hardware addition.   


### What is microchip, what is pubnub

[Microchip Technology]() is an American manufacturer of microcontroller, memory and analog semiconductors. Its products include microcontrollers and we are going to be focussing on the PIC32 series. 

[PubNub](http://www.pubnub.com) on the other hand is a global datastream network that lets you build and scale realtime applications for IOT, Mobile and web. 

By running PubNub on Microchip Technology's MCUs, you can build out realtime cloud connected embedded systems such as remote control of devices, push notifications, status updates and monitoring of home security systems, health monitoring and home automation systems.

### Demo concept

This demo shows you how to run PubNub on Microchip, in order to facilitate realtime communication between Microchip hardware and any other device, be it mobile or web. This will power IoT, allowing for bi-directional flow of data between different endpoints to and from Microchip hardware. I will show you how to control the LEDs on the [Ethernet starter Kit](http://www.microchip.com/DevelopmentTools/ProductDetails.aspx?PartNO=DM320004) from Microchip, and to send messages from the chip to the [PubNub Developer console](http://www.pubnub.com/console/). 

IMAGE FOR THE DEMO - JUST LIKE THE ATMEL ONE. 
IMAGE FOR PubNub + MICROCHIP 

EXPLAIN PUB SUB AND HOW PUBNUB WORKS.

http://g.recordit.co/nr3g85PC9O.gif 



## What do you need for this demo?
 

### Hardware required:

 - **PIC32 Ethernet Starter Kit** - The PIC32 Ethernet Starter Kit provides the easiest and lowest cost method to experience 10/100 Ethernet development with PIC32. The specific chip used on the board is PIC32MX795F512L.

 - Standard A to mini B cable for debugger
 - Standard A to micro B cable for USB application development
 
 - Ethernet cable
 - Hardware setup needs to be as follows:
 
 	
	 ![alt text](/images/hwsetup.jpg)
 
### Software required:

 - The **[Pubnub client library](https://github.com/pubnub/pic32-prod/tree/harmony)** on Github for the Microchip Harmony framework. 

 - **MPLAB® X IDE** is a software program that runs on a PC (Windows®, Mac OS®, Linux®) to develop applications for Microchip microcontrollers and digital signal controllers. It is called an Integrated Development Environment (IDE), because it provides a single integrated "environment" to develop code for embedded microcontrollers. 

 - **MPLAB® Harmony** is a comprehensive, interoperable, tested software development framework for Microchip's PIC32 microcontrollers. The framework integrates both internal and 3rd party middleware, drivers, peripheral libraries and real time operating systems, simplifying and accelerating the 32-bit development process.
 
MPLAB harmony is included to the IDE to simplify the development process for the PIC32 microcontrollers.


## How to run this demo?

### Prerequisites

1. Install the [MPLAB X IDE](http://www.microchip.com/mplabx) - v3.00.
2. Install [MPLAB Harmony](http://www.microchip.com/harmony) - v1.03.01.
3. Install the [MPLAB XC32 C/C++ Compiler](http://www.microchip.com/xc32).
4. Set up a working [PIC32 development platform](http://www.microchip.com/32bit).

 
#### Including MPLAB Harmony within MPLAB IDE

MPLAB Harmony provides a MPLAB Harmony Configurator (MHC) MPLAB-X IDE plug-in that can be installed in MPLAB X IDE to help you create your own MPLAB Harmony applications.

To create a new MPLAB Harmony application with MHC, follow these steps:


 - Start MPLAB X IDE and select Tools -> Plugins.
 - Select the Downloaded tab and click Add Plugins..., and then navigate to the MHC com-microchip-mplab-modules-mhc.nbm plug-in file, which is located in <install-dir>/utilities/mhc, and then click Open.

![alt text](/images/step12.png)

 - Ensure that the Install check box for the plug-in is selected and click Install.




![alt text](/images/step1.3.png)

 - Follow the prompts from the installation and continue until the installation completes. (Do not be concerned if the version you're installing is signed but not trusted, simply click Continue). Once the installation has finished you can close the Plugins dialog.
 
5. To verify the installation, select Tools > Plugins and select the Installed tab. The MHC plug-in you installed should be included in the list.


###Running the PubNub PIC32 Harmony project

To add Pubnub PIC32 Harmony library to your project, you have several options:

 - Add the library project
 - Add the generated library file
 - Add the files from the library

I am going to be choosing the **first option**. In any case, you have to link against the Harmony library, because that is what Pubnub PIC32 Harmony library uses. We use the TCPIP, TCPIP_DNS, SYS_TMR, and, optionally, TCPIP_SSL modules from Harmony. 



 - Go to the [Pic32 Github repository](https://github.com/pubnub/pic32-prod/tree/harmony) and download the zip file. 

2. Unzip/copy the contents of the library package to your Harmony apps directory. For example, on **Linux** this would be:

`~/microchip/harmony/v1_03_01/apps`


On **Windows**, this would be:

`c:\microchip\harmony\v1_03_01\apps`

This will create following basic directory structure under apps:

```
pubnub_client
    |
    +--pubnub_pic32_client
        |
        +--lib
        +--firmware

```

The lib directory contains the Pubnub client Harmony (static) library. The firmware directory contains a sample project you can load to your MPLABX IDE and try it "out of the box".

 - Running the pubnub client directly on the MPLAB IDE:

	 - Choose menu File|Open Project

	 - In the dialog that pops up, go to directory: c:\microchip\harmony\v1_03_01\apps\pubnub_client\pubnub_pic32_client\firmware

	- Then just click (not double-click) on the "pubnub_pic32_client.X". It is a directory, but, you'll see its icon is different than regular directories. It's actually a "project directory".

	- When you click it, in the "Project Name" box on the right of the directory tree you'll see the name of the project ("pubnub_pic32_client"). Click "Open Project" button in the lower right (above "Cancel").

	- When it loads (it will take a few seconds, you can monitor the progress in the status bar at the bottom of the window), first select the right configuration. The easiest way to do it is to go to the "command bar" (just under the menu) and click on the drop down box that is between the "Redo" and "Build Project" icons. You'll see three options:

		* pic32mx_eth_sk : choose this if you're using PIC32 Ethernet Starter Kit
		* pic32mx_eth_sk2 : choose this if you're using PIC32 Ethernet Starter Kit II
		* pic32mz_ec_sk : choose this if you're using PIC32MZ EC Starter Kit


 	- Choose SKDE PIC32 as the starter kit.

 	- Right click on the project name - `pubnub_pic32_client`, choose properties. Make sure the options chosen are as shown in the image below.

![alt text](/images/properties.png)

 - You should be all set up. Now choose menu Run|Run Project. It will build and then upload the firmware to the board and then reset it (so that FW starts executing). You can monitor this in the "Output" window, below the code editor window.
 
### Demo output
In order to see the output of this demo, open the [PubNub Developer Console](http://www.pubnub.com/console/), put in the **same** channel and the pub/sub keys as that in the code running in the IDE.
If all went well, then after a few seconds, you will see constant messages from the MCU. The message you send will be seen on the console, and you may send the following message:

```
{"led":{"2":1}}
```

to turn the LED number 2 ON. 

So, in general, the first number (quoted) is the number of the LED (on most boards there are LEDS 0 - 2), the second is 0 to turn OFF, or 1 to turn ON. So this should blink the LED 1:

```
{"led":{"1", 0}}
{"led":{"1", 1}}
{"led":{"1", 0}}
{"led":{"1", 1}}
```

On the debug console you will see periodic messages from the board as below: 

![alt text](/images/console.png)

As you can see, I have set the channel, pub and sub keys. The messages box shows me the messages I have sent, History gives me the messages sent and received and sent on the `channel` that I have set. Using the message box, I am able to send messages to the MCU to turn on and off the LEDs on the board itself.

### static to dynamic
In order to change from the static demo to the dynamic version, go to source files -> apps -> apps.c, make the following changes.
comment all the static demo functions such as pubnubStaticDemo.c(), PubnubStaticDemoInit() and PubnubStaticDemoProcess()
Add pubnubDemo.c, PubnubDemoInit, PubnubDemoProcess.
Now run the program, make sure you have the same channel and key names on the debug console. 


##Debugging : 

While running the program, if you choose the wrong starter kit(red bullet point), you wont see any thing happen. Make sure you choose a kit with a green bullet. 



Make sure you choose the right starter kit. 
MPLABX works like this: it has some "debug/run tool" saved in the project (the one last used). When you start debugging/running, it checks to see if the one from the project is available. If it is, cool, it proceeds to use it. If not, it will prompt you to choose one. Those red ones are the ones that are not available. 

The green ones (with a serial number) are the ones that are available that you can choose - of course, if there is more than one "green", you have to choose the right one, so it's best to have only one connected, so that you can't go wrong.

2.Available LEDs (on all starter kits) are LED 0, LED 1 and LED 2. So, never used LED "3" - it doesn't exist.
- On some Starter Kits / some configurations, some LEDs actually don't work. So, try them all.












