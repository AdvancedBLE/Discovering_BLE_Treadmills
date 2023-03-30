# Discovering how a BLE treadmill communicates
This guide will focus on how to find out how your treadmill communicates over Bluetooth (BLE). This enables one to understand what functionality your treadmill has via Bluetooth which can then be used to read and/or control it.

## Getting the basics.
To start with we will find out some basic informaiton about the treadmill Bluetooth. We will be using an app called nRF to help us find the needed information.

**nRF Connect app**
<a href="https://www.nordicsemi.com/Products/Development-tools/nrf-connect-for-mobile">Offical Website<a/> 

### Basic Info Guide
This guide will help us get:
1. Device Name
2. Services
<details>
  
  <summary>nRF Connect Android</summary>
  
  1. Install the nRF connect app <br>
  Note: make sure the treadmill is not connected to any devices or apps.<br>
  2. Click `SCAN`. This will scan all the available Bluetooth devices.<br>
  3. Find your treadmill in the list and click `CONNECT`.<br>
  You will now be connected to the treadmill via Bluetooth.<br>
  4. Make sure you are on the the `CLIENT` tab at the top.<br>
  5. 
  
</details>

<details>
  
  <summary>nRF Connect iOS</summary>
  1. Install the nRF connect app <br>
  Note: make sure the treadmill is not connected to any devices or apps.<br>
  2. Click `SCAN`. This will scan all the available Bluetooth devices.<br>
  3. Find your treadmill in the list and click `CONNECT`.<br>
  You will now be connected to the treadmill via Bluetooth.<br>
  4. Make sure you are on the the `CLIENT` tab at the top.<br>
  5. 
  
</details>

## Getting read and write information
The next steps will enable us to record how your treadmill is connecting, reading data and controllling the treadmill. This step can be a bit invloved but if followed step-by-step anyone can do it :-)

### Snooping
First things first. We will be listing to the Bluetooth communication. This called "snooping" and the process will be differtent depending on the device used. We will focus on using Andriod and iOS devices

<details>
  <summary>Android BLE Snooping</summary>
1.  Enable developer mode.<br>
Each manufacturer has their own steps to enable this but a quick Google will get you there.<br>
e.g. <a href="https://www.google.com/search?q=samsung+s22+enable+developer+mode">Google Search Example</a><br>
2.  Go to Settings<br>
3.  Go into developer options<br>
4.  Enable the option Enable Bluetooth HCI snoop log<br>
5.  restart your phone<br>
6.  Next we record some predefined communications. <br>
<a href="https://github.com/AdvancedBLE/Discovering_BLE_Treadmills/blob/main/README.md#test-process">test process</a> <br>
7.  Disable the option Enable Bluetooth HCI snoop log<br>
8.  In Developer Options: Bug report->Full report<br>
9.  Once completed a notification will appear at the top of the device. Click on it, share it via e.g. Discord. <br>
10. This zip file will contain the entire report. In the zip file look for the folder called **FS/Data/Log/bt**. This is the folder contains the raw Bluetooth communication.<br>

  
</details>

### Test process
In order to listing in on communications you will need to connect to an app that already works with your treadmill. The manufacturer usually has a basic app which you can use for this.

1.  Started the app and connected to your treadmill.
2.  Started an activity (5 km targed, starting speed 5.3 km/h, inclination: 1.50%)
3.  Start the activity
4.  Increased the speed in the app - up to 12.2 km/h (several steps between - because the app is awful!)
5.  Increased inclination in the app - up to 12.0% (several steps between - because the app is awful!)
6.  Increased the inclination at the treadmill to 15.0% (in 0.5% steps)
7.  Decreased the inclination at the treadmill to 0.0% (in 0.5% steps)
8.  Decreased the speed at the treadmill to 3.0 (in 0.1 km/h steps)
9.  Stopped the activity within the app and closed the app
10. Because the app is still keeping the connection I killed / forced stop the app

### Upload / Share
Now we can share/send the snooping files. 
