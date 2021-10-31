The following steps allow you to setup the Arduino IDE such that you can compile, modify and upload the code yourself.

# Preparation

## Arduino IDE

Get the latest Arduino IDE software from arduino.cc/en/Main/Software

## ESP32 support

File -> Preferences  (or Arduino -> Preferences on MacOS)

go to "Additional Board Manager URLs"

Add *https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json* and press OK

Tool -> Board -> Boards Manager

search for "esp32"

Install "esp32 by Espressif Systems"

**You need version 1.0.6. Version 2.0.0 is not yet supported**

## ESP32 Flash Filesystem Upload support

Get the zip file of the latest release from 
https://github.com/me-no-dev/arduino-esp32fs-plugin/releases/

Unzip the content to the tools folder of your Arduino IDE (~/Documents/Arduino/tools on MacOS,
similar on other OS) and restart IDE

# Install all required components

## Additional libraries

Select Tools -> Library Manager

Install "U8g2"

Install "MicroNMEA"

Install "GFX Library for Arduino"

## Additional libraries, part 2

From https://github.com/me-no-dev/ESPAsyncWebServer select "Download ZIP", extract to the libraries
folder of your Arduino IDE (~/Documents/Arduino/libraries on MacOS), rename main folder to ESPAsyncWebServer
(remove the "-master")

From https://github.com/me-no-dev/AsyncTCP select "Download ZIP", extract to the libraries folder
of your Arduino IDE, and rename main folder to AsyncTCP

Download https://github.com/lewisxhe/AXP202X_Library/archive/refs/tags/V1.1.3.zip
and extract to the libraries folder of your Arduino IDE

**NEW:**
* Download https://github.com/dx168b/async-mqtt-client/archive/master.zip
* Load the .zip file with Sketch → Include Library → Add .ZIP Library

## NO LONGER NEEDED: Additional libraries, part 3

For versions older than devel20210912 only:

Copy the libraries/SondeLib folder of this project to your Arduino IDE's libraries
folders, or, alternatively, create symbolic links (MacOS/Linux):

```
cd ~/Documents/Arduino/libraries
ln -s <whereyouclonedthegit>/rdz_ttgo_sonde/libraries/SondeLib/ .
```

Restart the Arduino IDE

(symbolic links are the preferred way, otherwise you have to copy the the libraries again after
each update)

# Final steps

In the IDE Tools -> Board: ->
Select "TTGO LoRa32-OLED v1" (or T-Beam, or something that fits your needs)

Compile and Upload code

Upload data to SPIFFS with Tools -> ESP32 Sketch Data Upload


