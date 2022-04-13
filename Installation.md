# Step-by-step description: Setting a up a new TTGO board

## Selecting a board and a display

See [[Supported boards]] for a more detailed discussion of all supported boards. Currently most people use
* The TTGO LORA v2.1_1.6 board (without integrated GPS)
* THe TTGO T-Beam v1.1 (with integrated GPS)

See [[Supported displays]] for more a more detailed discussion of all supported displays. Most popular choices:
* the 0.96" OLED 
* the 2.2" ILI9225 TFT

## Flashing the firmware

There is more than one way how to get the firmware on the board. Any one these alternatives will work:
* [[Binary installation]]: Use a more or less nice Windows GUI, or a command line tool (also on MacOS/Linux) to flash a firmware image that you can find on http://tdzsonde.mooo.com
* [[Arduino IDE installation]]: Use the Arudino IDE to compile the software yourself and then upload it
* [[PlatformIO installation]]: Use PlatformIO to compile the software yourself and then upload it (description is for the pio core - the simple command line version, you can also use some IDE frontend for platformIO (no documentation from me)
* [[ttgoconfig script]]: This is a Python script that directly can download and flash the firmware. Simple command line tool, needs Python.


## Initial configuration

On the first start after a full firmware flash, the board tries to do some automated detection/configuration. With the most common boards, it usually gets most of the common basic settings right, but there are cases you need to adjust yourself manually. The board will start WiFi in access point mode (SSID RDZsonde, password RDZsonde). Connect some device to that network and access http://192.168.4.1/.

* First, check [[Hardware configuration]]. 
  * For the 1.3" OLED and the ILI9341-TFT; you have to manually adjust the display type (others _should_ be detected automatically)
  * If you want to use buttons for controlling the TTGO: Autoconfig should set up the config for the physical buttons on most TTGO devices. If you add other buttons to some GPIO pins, you have to configure these manually.
  * If you add a GPS chip to TTGO boards without, you have to configure the GPIO pins manually
  * (i.e., in the simple cases, no need to do anything here)
* Second, making things look nice on your display: [[Display configuration]]
  * You can customize what is shown on your (OLED or TFT) display. For the OLED, the default configuration should be fine, for the TFT you can choose. First thing to do is to select the right screen config (1 for LED, 2 to 5 for TFT (portrait or landscape, normal or large)
  * After changing the screen config, reboot the TTGO
  * For the TFT, you can choose between several different screen layouts. You can put a number of "active" layouts in "Display screens". **For the TFT, you usually want to adjust this such that it looks as nice as you want it to be :-)**
  * The first layout is the "Scan screen" (used while not receiving something), all the others are a list of "Decode screens" that your used while receiving a sonde. You can use the button to switch between these layouts.
* Finally, optionally: Set up data feeds to external destinations
  * You first need to change WiFi to connect to some access point. For that you need to add SSID/password in the Network tab. The default behaviour (after a reboot) is to try to connect to a configured network first, and if that fails, go into access point mode.
  * [[Data feed configuration]] (APRS via TCP (wettersonde.net or radiosondy.info), AXUDP (for aprsmap), TNC mode (for APRSdroud)
  * [[MQTT configuration]] (for some MQTT server)
  * [[Chasemapper configuration]] (for the Chasemapper software)
  * [[SondeHub settings]] (for sondehub.org)
  * [[SondeHub import]] (Importing active RX frequencies from sondehub.org or other sites with same API)
