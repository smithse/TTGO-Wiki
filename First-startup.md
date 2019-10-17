## First startup (autoconfiguration)

The software will try to automatically detect the board type you are using (based on the state of some input pints on boot time). If you use a different board, additional things connected to your board, or a different wiring of external display, this might not work (it should work in the default configuration of all devices mentioned in [[Supported boards]]).

* TTGO Lora32 v1 / Heltec v1 / Heltec v2:
  * 0.9" OLED display connected to SDA=4, SCL=15 (RST=16)
  * Button1 on GPIO0, Button2 as touch input on GPIO13
* TTGO Lora32 v2.1:
  * 0.9" OLED display connected to SDA=21, SCL=22 (RST=16)
  * Button1 as touch input on GPIO2, Button2 as touch input on GPIO14
* TTGO T-Beam v0.7:
  * Button1 on GPIO39, Button2 as touch input on GPIO13
  * GPS RXD on GPIO34
  * (a) 0.9"/1.3" OLED display connected to SDA=21, SCL=22 (RST=16)
  * (b) SPI TFT display connected to SDA=4, CLK=21, RST=22, RS=2, CS=0
* TTGO T-Beam v1.0:
  * Button1 on GPIO38, Button2 disabled (will change in future)
  * GPS RXD on GPIO34
  * Power management controller on SDA=21, SCL=22
  * (a) 0.9"/1.3" OLED display connected to SDA=21, SCL=22 (RST=16)
  * (b) SPI TFT display connected to SDA=4, CLK=13, RST=14, RS=2, CS=0

## First configuration

After power up, the device will create a WiFi access point with SSID **RDZsonde** and password **RDZsonde**.
Connect your PC or phone to this access point.
You can also configure rdzTTGOsonde to connect to an existing WiFi network (see [[Wifi configuration]]).

In access point mode, you can then access the software using [http://192.168.4.1](http://192.168.4.1); if you configure rdzTTGOsonde to connect to an existing WiFi network, it will get an IP address from that network via DHCP.  In all cases, you can also access the board (if your browser supports mDNS) using the URL [http://rdzsonde.local](http://rdzsonde.local).


## System configuration (hardware)

On the configuration page, select the "Config" tab. If autoconfiguration does not select the right I/O pins automatically, you can adjust some hardware settings here (at the bottom of the page; changing these settings require restarting the board after saving the configuration):

* Display: 
  * Display type: 0 for the on-board SSD1306 0.9" OLED (or externally connected to T-Beam), 2 for the 1.3" OLED connected the same way as the 0.9", or 1 for the ILI9225-based TFT display
  * Configure OLED SDA and OLED SCL (and also OLED RST if a reset line is connected to your display) for the 0.9"/1.3" OLED displays
  * Configure TFT SDA, TFT CLK, TFT RST, TFT CS and TFT RS for SPI-based ILI9225 TFT display
* Buttons:
  * Up to two buttons are supported, you have to enter the GPIO number of the pins. If your supported board comes with an physical button, this button is automatically configured. You can add additional buttons, either "real" buttons, or use the touch button mode of ESP32 (in which you just connect a piece of wire to a pin and then just touch that pin). 
  * In touch mode, you might have to change the threshold value. Calibration currently is simply by trial and error.
* GPS:
  * If you have a GPS receiver on your board (on-board for a T-Beam, or external), rdzTTGOsonde can calculate distance and bearing from your current position to the received sonde. You have to configure which RXD pin the GPS is connected to.
