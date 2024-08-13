CS, MISO, MOSI, CLK
* Specify the pins where the SD card is connected (set to -1 to disable SD card interface)
* For the popular TTGO LoRa32 v2.1.6, the values are 13, 2, 15, 14
* Make sure to not re-use the pins otherwise (default config uses pins 2 and 14 as touch input pins)
* The code uses the HSPI interface (that is also used for the large SPI TFT displays). If you are using such a display, you have to use the same pins (for MISO, MOSI, CLK) as for the TFT display (and a different CS pin). The VSPI interface is used for the LoRa chip.

Sync interval: How often is data actually written to SD card (approximately). Tradeoff between data loss in case of power outage/crash and SD card wear.

Naming: 0: for each sonde id a new file is created with the id as file name; 1: each day a new file is created with the date as file name

You can acccess the sd card content at http://rdzsonde/sdfiles.html