# Clipboard Cloner

Traditional RFID badge cloning methods require you to be within 3 feet of your target, so how can you conduct a socially distanced physical penetration test and clone a badge if you must stay at least 6 feet from a person? Since 2020, companies have increasingly adopted a hybrid work environment, allowing employees to partially work remotely, which has decreased the amount of foot traffic in and out of a building at any given time. After throwing around some ideas, I thought, why not create a mobile long-range reader device that we could deploy early in the morning at a client site and let it do all the work for us.  This project guide contains an entry-level hardware design that you can build in a day and deploy in the field in order to increase your chances of remotely cloning an RFID badge. 

This is part of a full paper and talk given during **DEFCON 30** in the Physical Bypass Village and Radio Frequency Village titled: **Keeping Your Distance: Pwning RFID Physical Access Controls From 6FT and Beyond** by myself and Twitter: @_badcharacters (https://www.youtube.com/watch?v=OLLaXOcuYfw). 

The content has been updated for **DEFCON 31** titled: **Flipping Locks: Remote Badge Cloning with the Flipper Zero**. In this tutorial, you'll learn how to build you own Clipboard Cloner and clone the badge loot quickly and easily!

Here's the complete build guide for making your own Clipboard Cloner! 

 *Disclaimer:* **This guide is for educational and ethical hacking purposes ONLY. All penetration testing activities must be authorized by all relevant parties.**


# Clipboard Cloner Guide
Let's build the long-range reader cloning device. 
### Clipboard Cloner BOM: 
* ESP RFID Tool: https://hackerwarehouse.com/product/esp-rfid-tool/
* Low-Frequency Reader (e.g., HID Prox Pro 5355AGN00 Reader): Check eBay for used units
* Breadboard Jumper Wires - 3.9in (10cm): https://a.co/d/fja090p or 22AWG Wire: https://a.co/d/h7bbBom 
* 9V Rechargeable battery: https://www.amazon.com/dp/B0B9G9RQG3/ w/ T-Connector: https://www.amazon.com/dp/B07114RK67/
* OR 2x 3.7V 500mAh LiPo Batteries:https://www.amazon.com/gp/product/B07BTV3W87/ with a JST connector (https://www.amazon.com/gp/product/B07NWD5NTN/)
* 
* 3M Dual Lock Clear Velcro: https://a.co/d/gg4SzBd

### Wiring Guide 
Below is an example of the wiring guide to connect to a long-range reader with screw-in terminals using the ESP RFID Tool. Use the color-coded male-to-male breadboard wires to connect the two terminal interfaces between the Wiegand system and the ESP RFID Tool, as seen below.

<img src="https://user-images.githubusercontent.com/104524120/183313184-f8f62a73-4bb1-403b-8c65-bfd9d5edac78.PNG" width=80% height=80%>

* Then connect the 12V 5A DC Power Pigtail Barrel Plug Male Connector cable into the Wiegand system (HID iClass SE R90 pictured) and trail the cable to the outside of the reader so you can plug it into the 12V 6000mAh DC Battery. 

<img src="https://user-images.githubusercontent.com/104524120/183816676-e13ef2d6-b493-4d49-baa1-03c0f9d288a2.jpg" width=40% height=40%>

The same wiring applies to the low-frequency HID MaxiProx 5375 reader. 

<img src="https://github.com/sh0ckSec/RFID-Gooseneck/assets/104524120/1093738d-37ee-41df-a2d2-f16fe91940dd" width=40% height=40%>

Close-up of HID MaxiProx 5375 Wiring:

<img src="https://github.com/sh0ckSec/RFID-Gooseneck/assets/104524120/b3ee2581-b815-4f37-a525-e5853a5ddace" width=40% height=40%>

*WARNING:* Ensure when you are working with the HID MaxiProx 5375 that you change the jumper on the Shunt Pins settings from 2 and 3 +21-2.85 VDC (Default) TO Shunt Pins 1 and 2 +11.6-20.9VDC) because we are using a 12V battery. If you do not switch the jumper, you will fry the unit! YOU'VE BEEN WARNED! Double-check this for any reader you are working with, just in case. 

<img src="https://github.com/sh0ckSec/RFID-Gooseneck/assets/104524120/b41eb1ec-1524-4aae-b135-6da0f19b80b5" width=40% height=40%>

To remain as stealthy as possible, it is advised to turn off the audible "beep" if the reader allows you to. In this case, we can silence the beep on the HID MaxiProx 5375 reader by pushing down dipswitch #4 of SW1 (the farthest right of the switch sets). 

<img src="https://github.com/sh0ckSec/RFID-Gooseneck/assets/104524120/a1cb567d-821a-4a09-8444-d661cca4b558" width=40% height=40%>

*Image Source: http://exfil.co/2017/01/17/wiegotcha-rfid-thief/*


*Note: For various configurations, check out the official ESP RFID Tool wiring guide here: https://github.com/rfidtool/ESP-RFID-Tool/blob/master/Installation-Schematics/README.md*


# Battery Mounting
Once you have wired everything, take 3M Dual Lock Velcro and affix it to the back of the battery and the back of the reader. This will ensure the battery will stay firm throughout the engagement and it looks like it is part of the unit. 

HID MaxiProx 5375

<img src="https://github.com/sh0ckSec/RFID-Gooseneck/assets/104524120/b8f3ed3f-412c-4578-aa44-349defcdae07" width=40% height=40%>

HID R90 

<img src="https://github.com/sh0ckSec/RFID-Gooseneck/assets/104524120/f1c144d7-388c-406d-90e7-b537d8885114" width=40% height=40%>

HID R90 

<img src="https://github.com/sh0ckSec/RFID-Gooseneck/assets/104524120/dff98303-762d-467b-a10d-4417b1a18d12" width=40% height=40%>
          
# Mounting Reader to Pedestal
Depending on the reader, you must find the correct mounting hole guide for each. You will have to manually drill holes into the back of the reader in order to center it to the gooseneck pedestal with carriage bolts and nuts. Below is an example mount guide for the HID iCLASS R90.

<img src="https://user-images.githubusercontent.com/104524120/183313721-397f9938-6629-4a41-a248-e4815d4de5c0.PNG" width=40% height=40%>

iCLASS SE Mounting and User Guide: https://fccid.io/JQ6-ICLASSU90/User-Manual/User-Manual-2360366 

HID iClass R90 Gooseneck finished look: 

<img src="https://user-images.githubusercontent.com/104524120/183314105-ac8e840d-e4df-4971-92a6-41a3f69e5eaa.jpg" width=40% height=40%>

# NEW (UPDATED) - Cloning Low-Frequency Cards - Mobile Phone + Flipper Zero
To remain incognito while at the client site, cloning a card with a mobile phone and a Flipper Zero hidden away will keep the lowest profile rather than fiddling with a laptop when you need to copy the card data. 

### Mobile Cloning Gear:
* Mobile Phone (Android or iOS)
* Flipper Zero: https://shop.flipperzero.one/
* Flipper Mobile App: https://docs.flipper.net/mobile-app 
* RFID T5557 Rewritable Cards: https://a.co/d/0NF2zJG

<img src="https://github.com/sh0ckSec/RFID-Gooseneck/assets/104524120/c7e42376-441a-4686-9f8f-f9d90d8ce25a" width=40% height=40%>


### Step 1  - Access RFID Loot
Once the implant is in place and a few employees have walked past the gooseneck reader, hop onto your phone and log into your RFID ESP Key SSID to look for loot. The default SSID is "ESP-RFID-Tool" but it is recommended to change the name to something that will blend into the target environment. In order to change the SSID and password to protect the ESP RFID Tool wifi (and not leak all your client's credentials to the world), jump over to the configuration page to customize the settings and change all your default passwords. 
* Default SSID: **ESP-RFID-Tool**
* URL: http://192.168.1.1


Default credentials to access the configuration page:
* Username: *admin*
* Password: *rfidtool*

(Full ESP RFID Tool user guide here: https://github.com/rfidtool/ESP-RFID-Tool)

Once you're on the ESP RFID Tool WiFi, access Data in the "List Exfiltrated Data" Page:
<img src="https://user-images.githubusercontent.com/104524120/183313563-2b3c480d-2005-4bf0-b2db-7d00d182feda.PNG" width=50% height=50%>

### Step 2 - Copy the 2nd half of the Binary Payload and Convert to HEX
<img src="https://github.com/sh0ckSec/RFID-Gooseneck/assets/104524120/6aaf73ea-d200-47b5-8242-17cf173fc577" width=70% height=70%>

Copy the second half of the binary data: ​
* 10001111100000101001110011 ​
  
REMOVE the leading and trailing parity bits:
* ​000111110000010100111001

Take this and convert it into HEX using a Bin-HEX Converter ​on your phone:
* 000111110000010100111001 = 1F 05 39​


### Step 3 - Save your Card Data to the Flipper Zero

On your Flipper, **hit the center button** and navigate to > **125 hHz RFID** > **Add Manually**
![image](https://github.com/sh0ckSec/RFID-Gooseneck/assets/104524120/eff63263-fe18-485b-a2b1-a9dfd9aae3d1)


Then **Select HID H10301** > Enter the Data: **1F0539**
![image](https://github.com/sh0ckSec/RFID-Gooseneck/assets/104524120/f0e99f77-550a-4f46-8129-873e9e2936d1)


Select **Save** > **Name the card** (Enter the desired name)
![image](https://github.com/sh0ckSec/RFID-Gooseneck/assets/104524120/dc884af4-b73d-46e0-a134-7df90a78c0ba)

Select your saved card > **Info** (in order to look for your FC (Facility Code) and Card Number)
![image](https://github.com/sh0ckSec/RFID-Gooseneck/assets/104524120/08c9bf3c-a1bd-4589-af60-507343440057)


### Step 4- Clone your Card!
Select your saved card > **Write** it to a blank T5557 card
![image](https://github.com/sh0ckSec/RFID-Gooseneck/assets/104524120/bcdb096d-5250-4aa4-a2e7-81d8c48bd673)
In a few seconds...
![image](https://github.com/sh0ckSec/RFID-Gooseneck/assets/104524120/4a5bbf07-f7ab-455d-a98f-4fbc6c45aa8c)

Boom! Happy Hunting! 

![image](https://github.com/sh0ckSec/RFID-Gooseneck/assets/104524120/10bd4244-0146-4b59-b3f5-c6722533796d)

Special Shoutouts to the Bill Graydon of the Physical Security Village for hosting this talk during DEFCON 31!

# OLD METHOD - Cloning Low-Frequency Cards - Android Phone + Proxmark3 Easy 
**For the sake of documentation, I will leave the old method on this page. But finding the exact firmware for the Proxmark3 Easy can be tricky with now, unsupported AndProx App - it is highly recommended to use the Flipper Zero in the field for the easiest approach. You can use a Proxmark3RDV4 and use the Proxmark HEX from the ESP RFID Tool.**

To remain incognito while at the client site, cloning a card via an Android phone will keep the lowest profile rather than fiddling with a laptop when you need to copy the card data. 

<img src="https://user-images.githubusercontent.com/104524120/183313587-635d6993-c76d-49c7-9b92-a2122933511a.PNG" width=40% height=40%>

### Mobile Cloning Gear:
* Android Phone or Tablet of your choice
* AndProx Android App: https://github.com/AndProx/AndProx  
* Proxmark3 Easy (available on eBay or AliExpress)
* USB OTG Cable - Type C To Micro: https://a.co/d/4HGdBqh
* RFID T5557 Rewritable Cards: https://a.co/d/0NF2zJG
* 3D Printed Case (optional): https://www.thingiverse.com/thing:3123482 
                                                                                                                 
![MobileSetup](https://user-images.githubusercontent.com/104524120/183818120-04b57153-fbe9-4b91-b2df-90b1f6a31262.jpg)
                                                                                                          

### Step 1A  - Access RFID Loot
Once the implant is in place and a few employees have walked past the gooseneck reader, hop onto your phone and log into your RFID ESP Key SSID to look for loot. The default SSID is "ESP-RFID-Tool" but it is recommended to change the name to something that will blend into the target environment. In order to change the SSID and password to protect the ESP RFID Tool wifi (and not leak all your client's credentials to the world), jump over to the configuration page to customize the settings and change all your default passwords. 
* Default SSID: **ESP-RFID-Tool**
* URL: http://192.168.1.1


Default credentials to access the configuration page:
* Username: *admin*
* Password: *rfidtool*

(Full ESP RFID Tool user guide here: https://github.com/rfidtool/ESP-RFID-Tool)

Once you're on the ESP RFID Tool WiFi, access HEX Code Data in the "List Exfiltrated Data" Page:

<img src="https://user-images.githubusercontent.com/104524120/183313563-2b3c480d-2005-4bf0-b2db-7d00d182feda.PNG" width=50% height=50%>

### Step 1B - Copy the HEX Code Payload!

<img src="https://user-images.githubusercontent.com/104524120/183313560-a9b16ced-396f-4657-bc75-e541297411d2.PNG" width=70% height=70%>


### Step 2 - Android Cloning Setup
* Download and install AndProx (Root NOT required!): https://github.com/AndProx/AndProx 
* Plug in your Proxmark3 via OTG cable
* Click Connect Via USB
* Begin sending commands!

### Step 3 - AndProx Commands 
Once your Proxmark3 Easy is connected, copy your Hex Code and enter these commands: 

<img src="https://user-images.githubusercontent.com/104524120/183313638-804a3cc5-ddee-48dc-ab06-ab20b3baef0d.PNG" width=50% height=50%>

> lf hid clone [INSERT HEX CODE]

#Example: 
> lf hid clone 20043C0A73 

Verify your card data:
> lf search

<img src="https://user-images.githubusercontent.com/104524120/183313654-86c90889-5f66-4756-9d9a-b1d1330022e4.PNG" width=40% height=40%>


Boom! Happy Hunting!

<a href="https://www.buymeacoffee.com/sh0cksec" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>

# References
* Dib, Alex. "RFID Thief v2.0." July 2018, https://scund00r.com/all/rfid/tutorial/2018/07/12/rfid-theif-v2.html
* Farrell, Michael and Boris Hajduk. "AndProx." July 2021, GitHub, https://github.com/AndProx/AndProx
* Harding, Cory. "ESP-RFID-Tool." March 2018, GitHub, https://github.com/rfidtool/ESP-RFID-Tool
* Hughes, Nathan. "Flipper Maker" May 2022, https://flippermaker.github.io  ​
* Kelly, Mike. “Wiegotcha – RFID Thief” January 2017, https://exfil.co/2017/01/17/wiegotcha-rfid-thief/                     
* Rumble, Rich. "RFID Sniffing Under Your Nose and in Your Face." DerbyCon IX, September 2019, https://www.youtube.com/watch?v=y37j6RDtybQ
* W., Viktor. "Enclosure For Proxmark3 Easy." Thingiverse, September 2018, https://www.thingiverse.com/thing:3123482
* White, Brent and Tim Roberts. "Breaking Into Your Building: A Hacker's Guide to Unauthorized Access." NolaCon 2019, May 2019, https://www.youtube.com/watch?v=eft8PElmQZM 
