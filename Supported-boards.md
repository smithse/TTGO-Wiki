**Update**

Many new boards have come into the market, so some comments on what is supported and what is not:
- You need the 433 MHz version of any board.
- You need a board with SX1278 receiver chip. The SX1262/SX1268 chips are NOT supported. (If the label that is on the receiver model does not say SX1262 or SX1268, then it is usually the right one)
- There is support for boards with a simple charger chip, with the AXP192, and rudimentary (good enough) support for the AXP2101.
- You need a traditional ESP32 chip, the S3 is not directly supported (unless you compile the code yourself and do some minor changes)

Suggestions on some (probably still available) boards:
- Lilygo LoRa32 V2.1_1.6 (see below) - make sure to get the 433 MHz version (The similar T3S3 v1.0 is not supported, but seems like there is no 433 version of that board anyway). The board labelled T3_v1.6.1 is fine as well.
- Lilygo T-Beam v1.1 (with AXP192) and v1.2 (with AXP2101): There are two 433 MHz variants, one with SX1278 and one with SX1268. Only the first variant will work.
- Heltec Lora32 v2 is supported (if you still are able to get it), the newer Heltec Lora32 v3 has a SX1262 chip and is not supported!
- M5Stack Core2 board with Ra-02 based Lora board (M005)



**Important note (valid for all devices): _You need the 433 MHz version_ (the 433 MHz receiver is used as 403 MHz receiver). The 868/915 MHz version will not work!**

# Recommended boards:

## TTGO LORA v2.1_1.6

Advantages:
- Small board with on-board 0.96" OLED display 
- Great RF sensitivity (better then LORA v1.0 boards) - a BIG difference!
- SMA antenna connector (easier to connect external antenna)

Disadvantages:
- only reset button, no second button (but pins of the board can be configured as "touch pins", so just solder a small piece of wire and use it as button by touching it)


## TTGO T-BEAM 1.0 (new version, with charger IC AXP192)

Advantages:
- Also great RF sensitivity, quite the same as the board above
- Integrated GPS (allows displaying distance and direction to radiosonde)
- Integrated battery holder and charger (18650 cell)

Disadvantage(?):
- No integrated display (but, if you prefer a larger 1,3" OLED or 2" TFT display, its actually an advantage, as you can connect a display in your preferred size)
- Larger than other boards, adding a tiny flat LiPo to a v2.1 yields a more compact device

Note that some pins are used differently than on the older T-Beam v0.7. Instructions how to connect additional things you find on the internet for the v0.7 might not be correct for the v1.0.
- You can connect a I2C OLED display to pin 21/22 (SDA/SCL) the same way as you can with the old T-Beam 0.7
- You cannot swap SDA/SCL in software, because SDA/SCL is also used to communicate with the power management chip
- For the same reason, you should not connect a SPI display to pin 21/22 (you sometimes find such suggestion for T-Beam 0.7)

# Additional boards

The code has also been tested with the following boards:

## TTGO LoRa v1.0

First board supported, works fine, but sensitivity of 403 MHz reception is not as good as with other boards.
I got my board as "Wemos® TTGO LORA SX1278 ESP322 433 MHz" from Banggood in early 2019.  It seems to be identical to the "LILYGO TTGO LORA" currently sold by Banggood (untested).

The board has a second button (in addition to reset button) that can be used to control the software, and an on-board 0.96" OLED display.

The board has a tiny I-PEX connector on board for the antenna (so you need an adapter cable for connecting an antenna with a more common SMA connector).

Will not be supported in binary images after mid 2024. For newer versions you need to build your own firmware, configured for a 26 MHz ESP crystal.

## HELTEC TTGO LoRa v1

In terms of board layout (pin connections) from a software point of view very similar to TTGO LoRa v1.0.

No information on reception sensitivity compared to other boards.

Will not be supported in binary images after mid 2024. For newer versions you need to build your own firmware, configured for a 26 MHz ESP crystal.

## HELTEC TTGO LoRa v2

This board is very similar to the v1.0 board. Heltec states that RF impedance matching has been improved, so maybe better RF performance than the v1 board. Sensitivity not verified.

## TTGO T-BEAM (old version v0.7, TP5400 charger IC)

It is supported and can be a nice board after hardware modifications.

Advantages:
- On-board GPS. Allows you automatically display distance/direction to sonde

Advantages/Disadvantage:
- No integrated display (see T-Beam 1.0)

Disadvantages:
- Larger than the other boards
- Inconsistent quality. My board has two problems (but apparently other people have slightly better luck):
  * When connected to USB (in particular without battery in battery holder), the coil of the battery charger makes very annoying audible noise (seems like all boards are somewhat affected by this problems, but mine makes particular load noise, for others its just a little noise).
  * Battery charger chip causes HUGE RF interference in particular in battery-only operation. (https://vimeo.com/341131491)
  * Other people have reported that the board crashes right after booting / activating WiFi. My board is not affected, but if yours is, you can probably fix it by adding a larger stabilising capacitor to the power supply, as explained here: 
https://github.com/LilyGO/TTGO-T-Beam/issues/3


You can eliminate the quality problem by disabling the battery charger chip and directly connecting a battery to the 5V power supply. You cannot (should not in order to avaid hazards) charge the battery via USB after this modification.



# Final notes on different versions

In many online shops you can choose the frequency version as "color"

The 868/915 MHz version contains the SX1276 receiver chip. The chip supports both 433 MHZ and 868/915 MHz, but using different input pins. The board connects the antenna to the 868/915 MHZ input pin, the 433 MHz pin is unconnected. Theoretically the 868/915 MHZ version can be modified to work as 403 MHz receiver by directly connecting the antenna to the right pin of the chip, but this requires somewhat advanced SMD soldering skills...

So make sure to get the 433 version of the boards.