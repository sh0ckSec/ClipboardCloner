# Clipboard Cloner Guide
<img src="https://github.com/sh0ckSec/ClipboardCloner/assets/104524120/a7ce95e5-ea49-467b-8ba2-1c6a0fc96d1f" width=60% height=60%>

This project guide contains an entry-level hardware design that you can build in a day and deploy in the field in order to increase your chances of cloning an RFID badge for your red team and ethical hacking engagements.

Use this build and a simple social engineering interaction with a target. **"Hey, we're conducting a badge audit for our annual security audit. Can I see your badge?"** Once your target gives you their badge, you can simply hover it over the clipboard and hand it back within 1 second - you instantly copied their badge without them knowing any wiser.

This is part of an original full paper and talk given during **DEFCON 30** in the Physical Bypass Village **Keeping Your Distance: Pwning RFID Physical Access Controls From 6FT and Beyond** by myself and Twitter: @_badcharacters (https://www.youtube.com/watch?v=OLLaXOcuYfw). Each year (DEFCON 31, 32 and 33), the content is reiterated and improved upon, staying up on the latest techniques and gadgets to use in the field. The goal is to conduct a physical pen test without the need for a laptop, only a mobile phone and implant devices!

The content has been updated for **DEFCON 33** titled: **Flipping Locks: Remote Badge Cloning with the Flipper Zero and More**. In this tutorial, you'll learn how to clone the badge loot from your RFID Gooseneck reader quickly and easily!

<img width=20% height=20% alt="image" src="https://github.com/user-attachments/assets/8ac8bc0b-6389-4662-ad1e-db043406d98c" />

#### NOTE: iCLASS SE/SEOS Downgrade Attack and Legacy Attack Methods are updated in the latest slide deck from DEF CON 33 (2025) - download the .pdf to review the attack methods.


In this tutorial, you'll learn how to build your own Clipboard Cloner and clone the badge loot quickly and easily!

 *Disclaimer:* **This guide is for educational and ethical hacking purposes ONLY. All penetration testing activities must be authorized by all relevant parties.**

## Let's build it. 

<img src="https://github.com/sh0ckSec/ClipboardCloner/assets/104524120/d23fde5f-667a-41f6-9f36-e195921418f0" width=60% height=60%>


### Clipboard Cloner BOM: 

* Officemate Super Storage Supply Clipboard Case: https://www.amazon.com/gp/product/B07C66Z5RM/ 
* ESP RFID Tool: https://hackerwarehouse.com/product/esp-rfid-tool/
* Low-Frequency Reader (e.g., HID Prox Pro 5355AGN00 Reader): Check eBay for used units
* Breadboard Jumper Wires - 3.9in (10cm): https://a.co/d/fja090p or 22AWG Wire: https://a.co/d/h7bbBom 
* Clipboard Battery - 9V Rechargeable battery: https://www.amazon.com/dp/B0B9G9RQG3/ and 9V Battery Clip Connector: https://www.amazon.com/gp/product/B07P9HK38C/ 
* Wall Implant Batteries - 2x 3.7V 500mAh LiPo Batteries:https://www.amazon.com/gp/product/B07BTV3W87/ with a JST connector: https://www.amazon.com/gp/product/B07NWD5NTN/ AND a UY connector: https://www.amazon.com/gp/product/B071R2J7JP/
*  Low Voltage T-Connector: https://www.amazon.com/dp/B07114RK67/
*  3M Command Adhesive strip: https://www.amazon.com/dp/B004OKKVOC/

<img src="https://github.com/sh0ckSec/ClipboardCloner/assets/104524120/475620fb-08ff-4759-a034-fe06b957f9e8" width=80% height=80%>

Here's an example of the wire connections:

<img src="https://github.com/sh0ckSec/ClipboardCloner/assets/104524120/e219df78-ddc0-4055-9fc3-a6e81fe318bd" width=40% height=40%>

### Disable Beeping Sound
To remain as stealthy as possible, it is advised to turn off the audible "beep" if the reader allows you to. In this case, we can silence the beep on the HID Prox Pro 5355AGN00 reader by pushing down dipswitch SW-1 #2.

<img src="https://github.com/sh0ckSec/ClipboardCloner/assets/104524120/005a402b-085d-4d4e-872e-3a207afabe08" width=40% height=40%>

Flip switch SW-1 #2 down to turn off the beeping sound.

<img src="https://github.com/sh0ckSec/ClipboardCloner/assets/104524120/3c05b88c-a50c-40e2-9514-eb2b20a60e33" width=40% height=40%>

### Secure Parts to Clipboard
Use the 3M strips to secure it to the badge reader and the 9V inside of the clipboard so nothing jostles around while you're carrying it. 

<img src="https://github.com/sh0ckSec/ClipboardCloner/assets/104524120/cce51b6d-5af4-4c38-ab0e-c424e78744ce" width=30% height=30%>

Your final build will be sleek and sneaky.

<img src="https://github.com/sh0ckSec/ClipboardCloner/assets/104524120/5112e62e-3448-4596-b713-2477a3f40123" width=50% height=50%>


## Wall Implant Wiring Guide - 3.7V 500mAh LiPo Batteries
Let's take a look at the Wall Implant Remote badge cloner setup. If you want to create a wall implant to stick on a building, use LiPo batteries listed above so you can create an enclosed, all-in-one unit.

![Wall-ImplantCapture](https://github.com/sh0ckSec/ClipboardCloner/assets/104524120/f6b26e0e-a974-4908-b895-bad4cd0c31d8)


Below is an example of the wiring guide to connect to a HID reader with screw-in terminals using the ESP RFID Tool. Use the color-coded male-to-male breadboard wires to connect the two terminal interfaces between the Wiegand system and the ESP RFID Tool, as seen below. 
* Then connect the 2x 3.7V 600mAh LiPo Batteries in a series connection to power the reader and the ESP RFID Tool. These thin batteries will allow you to enclose all parts into the unit so it is nice and flat.
  
<img src="https://github.com/sh0ckSec/ClipboardCloner/assets/104524120/d6572f16-697a-4da9-8855-f46fd8b62908" width=80% height=80%>


Here is a picture of the wiring with the batteries connected.

![image](https://github.com/user-attachments/assets/b83251c7-7c44-4b61-9b87-fd4f0668ecbe)


Here's a picture with the batteries connected with an ESPKey Wiegand Interception Tool installed. (https://www.redteamtools.com/espkey)

<img src="https://github.com/sh0ckSec/ClipboardCloner/assets/104524120/bf01c506-b4f6-43f8-a690-97081265b833" width=40% height=40%>


*Note: For various configurations, check out the official ESP RFID Tool wiring guide here: https://github.com/rfidtool/ESP-RFID-Tool/blob/master/Installation-Schematics/README.md*

# Cloning Low-Frequency Cards - Mobile Phone + Flipper Zero
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

#### Note: Binary Code Breakdown 
It's not as crazy as you think, here's the breakdown of what the binary code means below:
<img width=70% height=70% alt="image" src="https://github.com/user-attachments/assets/015e5edc-cfad-42e9-a304-2f75f65fdd03" />
Source:  https://accessgrid.com/guides/access-control-protocols/examples-of-every-access-control-bit-format 

### Step 2 - Copy the 2nd half of the Binary Payload and Convert to HEX
The "HEX" in the loot file was designed for a Proxmark 3 device. The Flipper Zero takes a different type of hex code so here's how you get your payload to clone your card. 

<img width=70% height=70% alt="image" src="https://github.com/user-attachments/assets/5565aa65-4b93-4744-8b95-2fa29dea3a33" />


Copy the second half of the binary data: ​
* 00010000100000101001110011 ​
  
REMOVE the leading and trailing parity bits:
* 001000010000010100111001

Copy this and convert it into HEX using a Bin-HEX Converter ​on your phone and poof! You have the 6 digit hex code for your Flipper!
* 001000010000010100111001 = 21 05 39​


### Step 3 - Save your Card Data to the Flipper Zero

On your Flipper, **hit the center button** and navigate to > **125 hHz RFID** > **Add Manually**
![image](https://github.com/sh0ckSec/RFID-Gooseneck/assets/104524120/eff63263-fe18-485b-a2b1-a9dfd9aae3d1)


Then **Select HID H10301** > Enter the Data: **210539**
<img width=100% height=100% alt="image" src="https://github.com/user-attachments/assets/0e653e6e-8b92-4cfa-813b-0fd232679d16" />



Select **Save** > **Name the card** (Enter the desired name)
<img width=100% height=100% alt="image" src="https://github.com/user-attachments/assets/4041ce28-f4d0-4abd-8ade-a2dd9e177d8d" />


Select your saved card > **Info** (in order to look for your FC (Facility Code) and Card Number)
<img width=100% height=100% alt="image" src="https://github.com/user-attachments/assets/877b06b4-5fc9-4b41-9489-9920ef24b454" />



### Step 4- Clone your Card!
Select your saved card > **Write** it to a blank T5557 card
<img width=100% height=100% alt="image" src="https://github.com/user-attachments/assets/51a069ef-5677-4d2c-90b0-c3e7a35615e3" />

In a few seconds...
<img width=100% height=100% alt="image" src="https://github.com/user-attachments/assets/0bf89c44-f6bb-4a20-add9-b1e3fc6504b1" />


Boom! Happy Hunting! 
<p float="left">
<img src="https://github.com/user-attachments/assets/45b9e293-9ed4-4293-987f-37d882e52a54" width=20% height=20%>
          
![DC32](https://github.com/user-attachments/assets/8d56f4a6-3123-49d1-a24a-8314c1fa08e6)

![image](https://github.com/sh0ckSec/RFID-Gooseneck/assets/104524120/10bd4244-0146-4b59-b3f5-c6722533796d) 

</p>

Special Shoutouts to  the Physical Security Village team for hosting this talk during DEFCON!

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

* Bunsen, Auston. "Examples of every access control bit format." February 2025, https://accessgrid.com/guides/access-control-protocols/examples-of-every-access-control-bit-format 
* Farrell, Michael and Boris Hajduk. "AndProx." July 2021, GitHub, https://github.com/AndProx/AndProx
* Harding, Cory. "ESP-RFID-Tool." March 2018, GitHub, https://github.com/rfidtool/ESP-RFID-Tool
* Hughes, Nathan. "Flipper Maker" May 2022, https://flippermaker.github.io  
* Kelly, Mike. "Wiegotcha – RFID Thief." January 2017, https://exfil.co/2017/01/17/wiegotcha-rfid-thief/ 
* Phrack. “Flipper Zero RFID Thief” https://www.phrack.me/hardware/2025/02/26/Flipper-Zero-RFIDThief.html 
* Rumble, Rich. "RFID Sniffing Under Your Nose and in Your Face." DerbyCon IX, September 2019, https://www.youtube.com/watch?v=y37j6RDtybQ
* W., Viktor. "Enclosure For Proxmark3 Easy." Thingiverse, September 2018, https://www.thingiverse.com/thing:3123482
* White, Brent and Tim Roberts. "Breaking Into Your Building: A Hacker's Guide to Unauthorized Access." NolaCon 2019, May 2019, https://www.youtube.com/watch?v=eft8PElmQZM 
