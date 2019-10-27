## First startup (autoconfiguration)

The software will try to automatically detect the board type you are using (based on the state of some input pints on boot time). If you use a different board, additional things connected to your board, or a different wiring of external display, this might not work (it should work in the default configuration of all devices mentioned in [[Supported boards]]).

* TTGO Lora32 v1 / Heltec v1 / Heltec v2: (detected by GPIO16==0 on startup)
  * 0.9" OLED display connected to SDA=4, SCL=15 (RST=16)
  * Button1 on GPIO0, Button2 as touch input on GPIO13
* TTGO Lora32 v2.1: (detected by GPIO17==1 on startup)
  * 0.9" OLED display connected to SDA=21, SCL=22 (RST=16)
  * Button1 as touch input on GPIO2, Button2 as touch input on GPIO14
* TTGO T-Beam v0.7: (detected by GPIO12==1 on startup)
  * Button1 on GPIO39, Button2 as touch input on GPIO13
  * GPS RXD on GPIO12
  * (a) 0.9"/1.3" OLED display connected to SDA=21, SCL=22 (RST=16) (if GPIO21==1)
  * (b) SPI TFT display connected to SDA=4, CLK=21, RST=22, RS=2, CS=0 (if GPIO21==0)
* TTGO T-Beam v1.0: (otherwise)
  * Button1 on GPIO38, Button2 disabled (will change in future)
  * GPS RXD on GPIO34
  * Power management controller on SDA=21, SCL=22
  * (a) 0.9"/1.3" OLED display connected to SDA=21, SCL=22 (RST=16) (by I2C bus probe)
  * (b) SPI TFT display connected to SDA=4, CLK=13, RST=14, RS=2, CS=0

## First configuration

After power up, the device will create a WiFi access point with SSID **RDZsonde** and password **RDZsonde**.
Connect your PC or phone to this access point.
You can also configure rdzTTGOsonde to connect to an existing WiFi network (see [[Wifi configuration]]).

In access point mode, you can then access the software using [http://192.168.4.1](http://192.168.4.1); if you configure rdzTTGOsonde to connect to an existing WiFi network, it will get an IP address from that network via DHCP.  In all cases, you can also access the board (if your browser supports mDNS) using the URL [http://rdzsonde.local](http://rdzsonde.local).

