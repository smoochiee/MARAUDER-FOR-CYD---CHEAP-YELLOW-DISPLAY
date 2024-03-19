# **MARAUDER-FOR-CYD---CHEAP-YELLOW-DISPLAY**


##  **This is a tutorial on how you port marauder to your cyd devices**

### If you want a Webflash Installer go to [Fr4nkFletcher](https://github.com/Fr4nkFletcher/ESP32-Marauder-Cheap-Yellow-Display)



---
## PREPARING IDE SET UP  `IDE 2.2.1`
1. Install and open the the latest release of Arduino IDE
2. In the Arduino IDE, go to File>Preferences
3. Add the following URLs to Additional Boards Manager UR
- https://dl.espressif.com/dl/package_esp32_index.json
- https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_dev_index.json
4. Go to Tools>Board>Boards Manager, search for esp32 and install esp32 by Espressif Systems
  - Make sure it is version `2.0.10`
5. INSTALL THE [ CH340X Drivers](https://learn.sparkfun.com/tutorials/how-to-install-ch340-drivers/all)

---
## Multiple Definition of ieee80211_raw_frame_sanity_check 
 WE NEED TO EDIT ESP32 BOARD `platform.txt`
- OPEN ANY FOLDER ON YOUR DESKTOP
- COPY AND PASTE ON ADDRESS BAR SEE PICTURE BELOW :
-       C:\Users\USERNAME\AppData\Local\Arduino15\packages\esp32\hardware\esp32
- NOTE!!! YOU NEED TO CHANGE `USERNAME` ACCORDING TO YOUR username see  :
![copy paste](https://github.com/smoochiee/MARAUDER-FOR-CYD---CHEAP-YELLOW-DISPLAY/assets/30816448/0c5fbf73-f3e2-49dc-81dd-1c0571941c3c)


1. With any text editor open `platform.txt`
2. Add `-w` to the following compiler settings
- `build.extra_flags.esp32`
- `build.extra_flags.esp32s2`
- `build.extra_flags.esp32s3`
- `build.extra_flags.esp32c3`
3. Add `-zmuldefs` to the following compiler settings
- `compiler.c.elf.libs.esp32`
- `compiler.c.elf.libs.esp32s2`
- `compiler.c.elf.libs.esp32s3`
- `compiler.c.elf.libs.esp32c3`


---




## LIBRARY NEEDED FOR INSTALLATION   
[LIBRARIES](https://github.com/smoochiee/MARAUDER-FOR-CYD---CHEAP-YELLOW-DISPLAY/blob/main/libraries.zip) download and extra to your arduino library folder like this picture :
![libraries](https://github.com/smoochiee/MARAUDER-FOR-CYD---CHEAP-YELLOW-DISPLAY/assets/30816448/019e8df8-b1ba-4f48-9980-d94c43c0c3df)


---


## EDIT VALUE ON `USER_SETUP.H` ON TFT_ESPI_MASTER LIBRARY FOLDER ACCORDING TO YOUR TYPE OF CYD SEE PICTURE :

1. ONE USB CYD 

![1 USB](https://github.com/smoochiee/MARAUDER-FOR-CYD---CHEAP-YELLOW-DISPLAY/assets/30816448/97002eb9-49a4-4056-a080-696cf09d2c43)

2. TWO USB CYD

![2 USB](https://github.com/smoochiee/MARAUDER-FOR-CYD---CHEAP-YELLOW-DISPLAY/assets/30816448/37f05cab-d561-453b-a51b-6830da03d236)


---
## SOURCE CODE OF MARAUDER
1. GO TO [MARAUDER RELEASE](https://github.com/justcallmekoko/ESP32Marauder/releases) DOWNLOAD LATEST RELEASE
![SC](https://github.com/smoochiee/MARAUDER-FOR-CYD---CHEAP-YELLOW-DISPLAY/assets/30816448/d7b4e7c9-09ac-420c-8c30-687de588ea16)

   
2. UNZIP SOURCE CODE


## NOW WE EDIT SOME FILES ON ESP32 MARAUDER FOLDER OPEN WITH ANY TEXT EDITOR BUT PREFER USING [NOTE++](https://notepad-plus-plus.org/)
1. OPEN `CONFIG.H`
  - UNCOMMENT DEFINE `MARAUDER_V4`    
    ![DEFINE MARAUDER](https://github.com/smoochiee/MARAUDER-FOR-CYD---CHEAP-YELLOW-DISPLAY/assets/30816448/6cdaf830-0d81-4c6d-a62f-aa726024887b)

 - COMMENT OUT `#define HAS_TEMP_SENSOR` & `#define HAS_PWR_MGMT`  CYD DONT HAVE ONE AS PER GPS AND NEOPIXEL DONT MIND IT....
      ![IF DEF MARAUDER _V4](https://github.com/smoochiee/MARAUDER-FOR-CYD---CHEAP-YELLOW-DISPLAY/assets/30816448/61c97e4d-3225-401d-ade0-10e43567bbdb)


- DEFINE  KIT_LED_BUILTIN  TO  `#define KIT_LED_BUILTIN 17` AS PER CYD LED PIN STATED HERE [CYD PINS](https://github.com/witnessmenow/ESP32-Cheap-Yellow-Display/blob/main/PINS.md)
  

![LED](https://github.com/smoochiee/MARAUDER-FOR-CYD---CHEAP-YELLOW-DISPLAY/assets/30816448/601c4831-3189-472d-83ba-f6800e3964d0)


   
 - DEFINE SD_CS  TO `#define SD_CS 5`

![SD CS](https://github.com/smoochiee/MARAUDER-FOR-CYD---CHEAP-YELLOW-DISPLAY/assets/30816448/7d5aa31e-e58f-4053-9c14-1c1e754d9fad)

- DEFINE GPS PINS   `#define GPS_SERIAL_INDEX 2` ` #define GPS_TX 1`  `#define GPS_RX 3` SEE [Fr4nkFletcher](https://github.com/Fr4nkFletcher/ESP32-Marauder-Cheap-Yellow-Display/tree/master)FOR GPS

![GPS](https://github.com/smoochiee/MARAUDER-FOR-CYD---CHEAP-YELLOW-DISPLAY/assets/30816448/2e8787d0-3048-46ef-8035-67ae6f1d2138)


  - `DONT FORGET TO HIT SAVE!!!`
 ---

2. OPEN `DISPLAY.CPP` 

- DEFINE ` #ifdef TFT_SHIELD` TO `uint16_t calData[5] = { 350, 3465, 188, 3431, 2 };` 
![DISPLAYCPP](https://github.com/smoochiee/MARAUDER-FOR-CYD---CHEAP-YELLOW-DISPLAY/assets/30816448/68466006-29b4-4b84-9ca2-58449072b924)

- `DONT FORGET TO HIT SAVE!!!`

3. OPEN `MENUFUNCTIONS.CPP` 
 - DEFINE ` #ifdef TFT_SHIELD` TO `uint16_t calData[5] = { 350, 3465, 188, 3431, 2 };`
   ![MENUFUNCTIONS](https://github.com/smoochiee/MARAUDER-FOR-CYD---CHEAP-YELLOW-DISPLAY/assets/30816448/d4a11a22-7bd1-492c-98c6-9451e1511638)
- `DONT FORGET TO HIT SAVE!!!`

4. OPEN `WIFISCAN.CPP` YOU NEED TO DEFINE 3X SEE `LINE #` MAYBE DIFFER DEPENDS ON MARAUDER SOURCE UPDATE
 - DEFINE ` #ifdef TFT_SHIELD` TO  `uint16_t calData[5] = { 188, 3408, 286, 3498, 1 }; // Landscape TFT Shield`
   ![W1](https://github.com/smoochiee/MARAUDER-FOR-CYD---CHEAP-YELLOW-DISPLAY/assets/30816448/6ecbe12e-aac9-4a21-aee2-61a10042e0e2)
- DEFINE  ` #ifdef TFT_SHIELD` TO  `uint16_t calData[5] = { 188, 3408, 286, 3498, 1 }; // Landscape TFT Shield`
![W2](https://github.com/smoochiee/MARAUDER-FOR-CYD---CHEAP-YELLOW-DISPLAY/assets/30816448/191f7d7c-4520-4380-8fdb-784479b07869)

- DEFINE ` #ifdef TFT_SHIELD` TO  `uint16_t calData[5] = { 188, 3408, 286, 3498, 1 }; // Landscape TFT Shield`
![W3](https://github.com/smoochiee/MARAUDER-FOR-CYD---CHEAP-YELLOW-DISPLAY/assets/30816448/2177fce2-4664-4b86-ac62-9a9c87ed0006)

- `DONT FORGET TO HIT SAVE!!!`
---
  

## SETTING UP IDE FOR COMPILATION  GO TO ` TOOLS `TAB

- FOR BOARDS WE CHOOSE `LOLIN D32`
- FOR PORT DEPENDS ON YOUR VALUE `COM#` ON YOUR DEVICE MANAGER

  
  ![COM PORT](https://github.com/smoochiee/MARAUDER-FOR-CYD---CHEAP-YELLOW-DISPLAY/assets/30816448/7594ebbc-f253-4c9d-ae16-6afad7ae95fd)
- PARTITION SCHEME SET TO MINIMAL SPIFFS (LARGE APP WITH OTA)

- UPLOAD SPEED TO `115200` IF YOU HAVE PROBLEM WITH UPLOADING

![IDE](https://github.com/smoochiee/MARAUDER-FOR-CYD---CHEAP-YELLOW-DISPLAY/assets/30816448/3e767abc-c7d0-4e01-a67d-6de825e26af9)


## MAKING BIN FILE IF YOU NEED  GO TO `SKETCH` TAB AND SELECT `EXPORT COMPILED BINARY`
 ![bin](https://github.com/smoochiee/MARAUDER-FOR-CYD---CHEAP-YELLOW-DISPLAY/assets/30816448/31e7d53c-2002-4f02-a1b4-72abdf77b28e)

 - BUILD OUTPUT IS ON BUILD FOLDER 
   


![buildbin](https://github.com/smoochiee/MARAUDER-FOR-CYD---CHEAP-YELLOW-DISPLAY/assets/30816448/92622215-f8ad-48bf-9053-a6ab1ff7fc44)



## FOR MODDING SPLASH SCREEN GO TO [MARAUDER SPLASH MOD](https://github.com/smoochiee/esp32-Marauder-mod-CYD)


# IF YOU HAVE ERRORS SEE [MARAUDER WIKI FAQ](https://github.com/justcallmekoko/ESP32Marauder/wiki/faq)


## Acknowledgments

A big shoutout to the creators and supporters of the ESP32 Cheap Yellow Display project and the community Discord, 
especially
[Fr4nkFletcher](https://github.com/Fr4nkFletcher/ESP32-Marauder-Cheap-Yellow-Display) and [ggaljoen](https://github.com/ggaljoen) for Tft_espi Library. 
And of course JustCallMeKoko for the foundational work on the ESP32 Marauder. 
THANK YOU `ATOMNFT.ETH` FOR DONATIONS.
     

# DONATION
**If you like you can donate to MY PAYPAL ACCOUNT :**


[PAYPAL](https://paypal.me/smoochieelee?country.x=PH&locale.x=en_US)
or
[GCASH](https://github.com/smoochiee/Ble-jammer/blob/main/GCash-MyQR-16032024181536.PNG.jpg)






