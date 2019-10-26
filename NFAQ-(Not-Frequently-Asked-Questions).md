# I want to extract files from the ESP32, how can I do that?

Easy...

First you need to find out where the SPIFFS is in your image (if you use images from rdzsonde.moo.com, its probably at 0x291000; if you are using a recent version of the Arduino IDE, its probably at 0x290000).  You can just pick a value and try, or you can read the ESP's partition table:

```
python <path>/esptool.py -p <port> -b 460800 read_flash 0x8000 0xC000 parttable.bin
python <path>/gen_esp32part.py parttable.bin parttable.csv
grep spiffs parttable.csv
```
(replace `<path>` with the place where these two tools are installed, and `<port>` with the serial port your board is connected to). You should get an output such as:
```
spiffs,data,spiffs,0x290000,1472K,
```

Second, you can extract the SPI flash file system (if your starting address is different to 0x290000, replace 0x290000 with the address you obtained above, and 0x170000 with the size until the end of the flash (0x400000-start address, this is 0x16F000 for start at 0x291000):
```
python esptool.py -p /dev/tty.SLAB_USBtoUART -b 460800 read_flash 0x290000 0x170000 flash.bin
mkspiffs -b 4096 -p 256 -s 1507328 -u out flash.bin
```
You will get all files in the "out" folder.