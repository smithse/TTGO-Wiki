# Welcome to the rdz_ttgo_sonde wiki!

## Introduction

This software turns simple ESP32 boards with SX127x-LoRa-Chip and OLED display into a portable receiver for radiosondes.

Boards that have been tested
- TTGO LoRa32 v1.0 (less sensitive than v2 boards)
- TTGO LoRa32 v2.1
- TTGO T-BEAM
The software should automatically configure the OLED ports for those two boards.

- If you have a similar board, but Display and/or buttons are not working, you have to manually configure the values (port numbers) of button_pin, oled_sda, oled_scl=22
Let me know if you sucessfully use this software on another board, and I will add it here

## Installation

You can find installation instructions for binary images at http://rdzsonde.mooo.com

Alternatively, the Setup.mp in the main repository explains how to set up the Arduino IDE for compiling and uploading this code to the LoRa32 boards.