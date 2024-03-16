# MARAUDER-FOR-CYD---CHEAP-YELLOW-DISPLAY
**This is a tutorial on how you port marauder to your cyd devices**

---
# PREPARING IDE SET UP
1. Install and open the the latest release of Arduino IDE
2. In the Arduino IDE, go to File>Preferences
3. Add the following URLs to Additional Boards Manager UR
- https://dl.espressif.com/dl/package_esp32_index.json
- https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_dev_index.json
4. Go to Tools>Board>Boards Manager, search for esp32 and install esp32 by Espressif Systems
  - Make sure it is version `2.0.11`
5. Install the CP210X Drivers
6. INSTALL THE [ CH340X Drivers](https://learn.sparkfun.com/tutorials/how-to-install-ch340-drivers/all)

---
# Multiple Definition of ieee80211_raw_frame_sanity_check 
 WE NEED TO EDIT ESP32 BOARD `platform.txt`
- COPY AND PASTE ON ADDRESS BAR SEE PICTURE BELOW :
-       C:\Users\USERNAME\AppData\Local\Arduino15\packages\esp32\hardware\esp32\2.0.11
- NOTE!!! YOU NEED TO CHANGE `USERNAME` ACCORDING TO YOUR username see  :
-![copy paste](https://github.com/smoochiee/MARAUDER-FOR-CYD---CHEAP-YELLOW-DISPLAY/assets/30816448/a24504e4-fea4-49d9-8314-1561f0b74cd9)

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




# LIBRARY NEEDED FOR INSTALLATION 
[LIBRARIES](https://github.com/smoochiee/MARAUDER-FOR-CYD---CHEAP-YELLOW-DISPLAY/blob/main/libraries.zip) download and extra to your arduino library folder like this picture :
![libraries](https://github.com/smoochiee/MARAUDER-FOR-CYD---CHEAP-YELLOW-DISPLAY/assets/30816448/019e8df8-b1ba-4f48-9980-d94c43c0c3df)


---


# EDIT VALUE ON `USER_SETUP.H` ON TFT_ESPI_MASTER LIBRARY FOLDER ACCORDING TO YOUR TYPE OF CYD SEE PICTURE :





1. ONE USB CYD 




