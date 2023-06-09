# How to discover BLE treadmill communications
This guide will focus on how to find out how your treadmill communicates over Bluetooth (BLE). This enables one to understand what functionality your treadmill has via Bluetooth which can then be used to read and/or control it.

## Getting the basics
To start with we will find out some basic informaiton about the treadmill Bluetooth. We will be using an app called nRF Connect to help us find the needed information.

**nRF Connect app**
<a href="https://www.nordicsemi.com/Products/Development-tools/nrf-connect-for-mobile">Offical Website<a/> 

### Basic Info Guide
This guide will help us get:
1. Device Name/Complete Local Name
2. Services
3. Characteristics
<details>
  
  <summary>nRF Connect Android</summary>
  
  1. Install the nRF Connect app <br>
  Note: make sure the treadmill is not connected to any devices or apps.<br>
  2. Click `SCAN`. This will scan all the available Bluetooth devices.<br>
  You should now see your treadmill listed in the device list under the `SCANNER` tab.<br>
  3. Click on the device name. Will will expand and provide some more information. You are looking for the following:<br>
  <strong>Complete Local Name<br>
    Service Data<br></strong>
  Take a screen shot of this information.<br>
  Next we will find the Characteristics. <br>
  4. Click the `CONNECT` next to your device name.<br>
  You will now be connected to the treadmill via Bluetooth.<br>
  5. Make sure you are on the the `CLIENT` tab at the top.<br>
  6. You will see a number of headings. Open each heading and take note of any containing the word `Characteristics`. <br>
  Take a screen shot of this information.<br>
    
</details>

<details>
  
  <summary>nRF Connect iOS</summary>
  1. Coming Soon
  
</details>

## Getting read and write information
The next steps will enable us to record how your treadmill is connecting, reading data and controllling the treadmill. This step can be a bit involved but if followed step-by-step anyone can do it :-)

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
5.  Restart your phone<br>
6.  Next record a predefined communicaiton steps with the treadmill
<a href="https://github.com/AdvancedBLE/Discovering_BLE_Treadmills/blob/main/README.md#test-process">(test process).</a> <br>
7.  Disable the option Enable Bluetooth HCI snoop log<br>
8.  In Developer Options: Bug report->Full report<br>
9.  Once completed a notification will appear at the top of the device. Click on it, share it via e.g. Discord. <br>
10. This zip file will contain the entire report. In the zip file look for the folder called **FS/Data/Log/bt**. This is the folder contains the raw Bluetooth communication.<br>
  
</details>
  
<details>
<summary>iOS BLE Snooping</summary>
  
1.  Coming Soon
Resources - https://www.bluetooth.com/blog/a-new-way-to-debug-iosbluetooth-applications/
  
</details>

### Test process
In order to listing in on communications you will need to connect to an app that already works with your treadmill. The manufacturer usually has a basic app which you can use for this.

1.  Started the app and connected to your treadmill.
2.  Start the treadmill, ideally via the app then set:
    - speed: 5.3 km/h
    - incline: 1.50%
3.  Increased the speed in the app - up to 12.2 km/h
4.  Increased incline in the app - up to 12.0%
5.  Increased the incline in the app to 15.0% (in 0.5% steps)
6.  Decreased the incline in the app to 0.0% (in 0.5% steps)
7.  Decreased the speed in the app to 3.0 (in 0.1 km/h steps)
8.  Stopped the activity within the app and closed the app
9.  Because the app is still keeping the connection I killed / forced stop the app
