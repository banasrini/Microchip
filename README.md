DOCUMENTED IN THE ORDER THAT i INSTALLED AND RAN THE PROGRAM

Blog headings

### Introduction

At PubNub, we are always trying to integrate with new hardware and this time it is Microchip Technology. The number of platforms we support only keep increasing everyday, and we are super excited to announce this latest hardware addition.   


### what is microchip, what is pubnub

Microchip Technology is an American manufacturer of microcontroller, memory and analog semiconductors. Its products include microcontrollers and we are going to be focussing on the PIC32 series. PubNub on the other hand is a [global datastream network](http://www.pubnub.com) that lets you build and scale realtime applications for IOT, Mobile and web. With PubNub and Microchip you can build out cloud connected embedded systems. Remote control of devices, push notifications, status updates and monitoring of home security systems, health monitoring and home automation systems are some of the cool projects that can be built by this collaboration.

### what the demo is about- concept

This demo takes you through the initial steps of running the MPLAB harmony IDE
### what are the applications of this collaboration

##OVERALL STEPS TO RUN THE DEMO

* install mplab ide and harmony and the compiler.
* include the mph plugin into the ide.
* open the pubnub demo and place into c:\microchip\harmony\v1_03_01\apps
* load & run the example into the MPLABX IDE.

##STEPS IN DETAIL : 

### hardware
PIC32MX795F512L chip 

PIC32 Ethernet Starter Board - This board provides a low-cost, modular development system for Microchip’s line of 32-bit microcontrollers.

Standard A to mini B cable for debugger
Standard A to micro B cable for USB application development
Ethernet cable
### software 


MPLAB® X IDE is a software program that runs on a PC (Windows®, Mac OS®, Linux®) to develop applications for Microchip microcontrollers and digital signal controllers. It is called an Integrated Development Environment (IDE), because it provides a single integrated "environment" to develop code for embedded microcontrollers. 

MPLAB® Harmony is a comprehensive, interoperable, tested software development framework for Microchip's PIC32 microcontrollers. The framework integrates both internal and 3rd party middleware, drivers, peripheral libraries and real time operating systems, simplifying and accelerating the 32-bit development process.

We are including MPLAB harmony to the IDE to simplify the development process for the PIC32 microcontrollers.


###Step 1: Prerequisites

1. Install the [MPLAB X IDE] (http://www.microchip.com/mplabx) - v3.00.
2. Install [MPLAB Harmony] (http://www.microchip.com/harmony) - v1.03.01.
3. Install the [MPLAB XC32 C/C++ Compiler] (http://www.microchip.com/xc32).
4. Set up a working [PIC32 development platform] (http://www.microchip.com/32bit) PIC32MX795F512L CAN BE USED AS PART OF THE ETHERNET STARTUP KIT. (http://www.microchip.com/DevelopmentTools/ProductDetails.aspx?PartNO=DM320004).
 



###Introduction to Mplab harmony


MPLAB Harmony provides a MPLAB Harmony Configurator (MHC) MPLAB-X IDE plug-in that can be installed in MPLAB X IDE to help you create your own MPLAB Harmony applications.

To create a new MPLAB Harmony application with MHC, follow these four steps:

**• Step 1: Install MHC**

1. Start MPLAB X IDE and select Tools > Plugins.
2. Select the Downloaded tab and click Add Plugins..., and then navigate to the MHC com-microchip-mplab-modules-mhc.nbm plug-in file, which is located in <install-dir>/utilities/mhc, and then click Open.

![alt text](/images/step12.png)


3. Ensure that the Install check box for the plug-in is selected and click Install.

4. Follow the prompts from the installation and continue until the installation completes. (Do not be concerned if the version you're installing is signed but not trusted, simply click Continue). Once the installation has finished you can close the Plugins dialog.
5. To verify the installation, select Tools > Plugins and select the Installed tab. The MHC plug-in you installed should be included in the list.

**• Step 2: Create the New Harmony Project**


1. Select File > New Project or click the New Project icon in MPLAB X IDE.

2. In Categories, select Microchip Embedded and in Projects select MPLAB Harmony Project from the list of available project templates, and then click Next to launch the Microchip Harmony Configurator Project Wizard.

3. Specify the following in the New Project dialog:

	• Harmony Path (path to the folder containing Harmony framework: <install-dir>)

	• Project Location (the default project path is the apps folder within the selected MPLAB 	Harmony path)

	• Project Name

	• Configuration Name (optional)

	• Target Device (when a valid harmony path is selected, the device selection menu will be 	filled)




###Step 3: Getting Started 

Unzip/copy the contents of the library package to your Harmony apps directory. For example, on Linux this would be:
~/microchip/harmony/v1_03_01/apps


On Windows, this would be:
c:\microchip\harmony\v1_03_01\apps


Of course, you may unzip/copy to some other version of Harmony (other than v1_03_01).
This will create following basic directory structure under apps:
pubnub_client
    |
    +--pubnub_pic32_client
        |
        +--lib
        +--firmware


The lib directory contains the Pubnub client Harmony (static) library. The firmware directory contains a sample project you can load to your MPLABX IDE and try it "out of the box".
Step 3: running the pubnub client directly on the mplab ide  : 
- Choose menu File|Open Project

- In the dialog that pops up, go to directory: c:\microchip\harmony\v1_03_01\apps\pubnub_client\pubnub_pic32_client\firmware

- Then just click (not double-click) on the "pubnub_pic32_client.X" (it's possible that there is a typo, and it says "pubnup_pic32_client.X" :) ). It is a directory, but, you'll see its icon is different than regular directories. It's actually a "project directory".

- When you click it, in the "Project Name" box on the right of the directory tree you'll see the name of the project ("pubnub_pic32_client"). Click "Open Project" button in the lower right (above "Cancel").

- When it loads (it will take a few seconds, you can monitor the progress in the status bar at the bottom of the window), first select the right configuration. The easiest way to do it is to go to the "command bar" (just under the menu) and click on the drop down box that is between the "Redo" and "Build Project" icons. You'll see three options:

* pic32mx_eth_sk : choose this if you're using PIC32 Ethernet Starter Kit
* pic32mx_eth_sk2 : choose this if you're using PIC32 Ethernet Starter Kit II
* pic32mz_ec_sk : choose this if you're using PIC32MZ EC Starter Kit



Choose SKDE PIC32 as the starter kit.
- Of course, have your dev board (Starter Kit) attached to an USB port.

- You should be all set up. Now choose menu Run|Run Project. It will build and then upload the firmware to the board and then reset it (so that FW starts executing). You can monitor this in the "Output" window, below the code editor window.

On the debug console you will see periodic messages from the board as below: 

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












