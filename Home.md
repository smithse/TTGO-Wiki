# Welcome to the rdz_ttgo_sonde wiki!

## Introduction

This software turns simple ESP32 boards with SX127x-LoRa-Chip and OLED display into a portable receiver for radiosondes.

Boards that have been tested
- TTGO LoRa32 v1.0 (less sensitive than v2 boards)
- TTGO LoRa32 v2.1
The software should automatically configure the OLED ports for those two boards.

- It has also been reported to work correctly with the TTGO T-BEAM board, but auto-configuration does not yet work. You have to manually configure button_pin=39, oled_sda=21, oled_scl=22
- possibly some other? let me know if you sucessfully use this software on another board, and I will add it here

## Installation

You can find installation instructions for binary images at http://rdzsonde.my.to

Alternatively, the Setup.mp in the main repository explains how to set up the Arduino IDE for compiling and uploading this code to the LoRa32 boards.