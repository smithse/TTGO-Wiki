The code has been tested with the following boards:

## TTGO LoRa v1.0

First board supported, works fine, but sensitivity of 403 MHz reception is not as good as with other boards.
I got my board as "Wemos® TTGO LORA SX1278 ESP322 433 MHz" from Banggood in early 2019.  It seems to be identical to the "LILYGO TTGO LORA" currently sold by Banggood (untested).

The board has a second button (in addition to reset button) that can be used to control the software, and an on-board 0.96" OLED display.

The board has a tiny I-PEX connector on board for the antenna (so you need an adapter cable for connecting an antenna with a more common SMA connector)

## HELTEC TTGO LoRa

In terms of board layout (pin connections) from a software point of view very similar to TTGO LoRa v1.0.

No information on reception sensitivity compared to other boards.


## TTGO LORA v2.1_1.6

My personal preference. On-board 0.96" display

Advantages:
- superior RF sensitivity (compared to v1.0 boards) - a BIG difference!
- SMA antenna connector (easier to connect external antenna)

Disadvantages:
- no second button (but pins of the board can be configured as "touch pins", so just solder a small piece of wire and use it as button by touching it

Important note (valid also for other devices, but very often this board is sold as 868 MHz version): **You need the 433 MHz version** (the 433 MHz receiver is used as 403 MHz receiver).
The 868/915 MHz version will not work!

(Detailed version: The 868/915 MHz version contains the SX1276 receiver chip. The chip supports both 433 MHZ and 868/915 MHz, but using different input pins. The board connects the antenna to the 868/915 MHZ input pin, the 433 MHz pin is unconnected. Theoretically the 868/915 MHZ version can be modified to work as 403 MHz receiver by directly connecting the antenna to the right pin of the chip, but this requires somewhat advanced SMD soldering skills...)


## TTGO T-BEAM (old version, TP5400 charger IC)

It is supported and **might** be a nice board.

Advantages:
- On-board GPS. Allows you automatically display distance/direction to sonde
- Integrated battery holder (for 16850 battery)

Advantages/Disadvantage:
- No on-board display. You can easily add an display (a 0.96" display fits nicely. If you get the right version, the order of pins on display and T-BEAM match, so it is really easy to connect - for some 0.96" display versions you need to re-order the pins). One advantage might be that you can optionally add a larger display (e.g., an 1.3" display with SSD1306 controller works fine)

Note: currently my software does not support displays with other controller chips. I have a 2.0" display with ILI9225 controller at home, and  maybe I will try adding support for that board some time in the future.

Disadvantages:
- Larger than the other boards, adding a tiny flat LiPo to a v1.0 or v2.1 yields a more compact device
- Inconsistent quality. My board has two problems (but apparently other people have better luck):
  * When connected to USB (in particular without battery in battery holder), the coil of the battery charger makes very annoying audible noise (seems like all boards are somewhat affected by this problems, but mine makes particular load noise, for others its just a little noise).
  * Battery charger chip causes HUGE RF interference in particular in battery-only operation. (https://vimeo.com/341131491)

You can eliminate the quality problem by disabling the battery charger chip and directly connecting a battery to the 5V power supply. You cannot (should not in order to avaid hazards) charge the battery via USB after this modification.

## TTGO T-BEAM (new version, charger IC AXP192)

There is an updated revision of the board, LiliyGo claims that this update removes the power/noise problems mentioned above.  The charging circuit was completely replaced, so this is likely to be true. 

NOT YET TESTED, please send me your experience reports if you have such a board.
