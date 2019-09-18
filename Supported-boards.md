The code has been tested with the following boards:

## TTGO LoRa v1.0

First board supported, works fine, but sensitivity of 403 MHz reception is not as good as with other boards.
I got my board as "Wemos® TTGO LORA SX1278 ESP322 433 MHz" from Banggood in early 2019.  It seems to be identical to the "LILYGO TTGO LORA" currently sold by Banggood (untested).

The board has a second button (in addition to reset button) that can be used to control the software, and an on-board 0.96" OLED display.

The board has a tiny I-PEX connector on board for the antenna (so you need an adapter cable for connecting an antenna with a more common SMA connector)

## HELTEC TTGO LoRa

In terms of board layout (pin connections) from a software point of view very similar to TTGO LoRa v1.0. No data on reception sensitivity compared to other boards.


## TTGO LORA v2.1_1.6

My personal preference. On-board 0.95" display

Advantages:
- superior RF sensitivity (compared to v1.0 boards) - a BIG difference!
- SMA antenna connector (easier to connect external antenna)

Disadvantages:
- no second button (but pins of the board can be configured as "touch pins", so just solder a small piece of wire and use it as button by touching it

Important note (valid also for other devices, but very often this board is sold as 868 MHz version):

**You need the 433 MHz version ** (the 433 MHz receiver is used as 403 MHz receiver).
The 868/915 MHz will not work!

(Detailed version: The 868/915 MHz version contains the SX1276 receiver chip. The chip supports both 433 MHZ and 868/915 MHz, but using different input pins. The board connects the antenna to the 868/915 MHZ input pin, the 433 MHz pin is unconnected. Theoretically the 868/915 MHZ version can be modified to work as 403 MHz receiver by directly connecting the antenna to the right pin of the chip, but this requires somewhat advanced SMD soldering skills...)

## TTGO T-BEAM