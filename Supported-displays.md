# Supported displays

## OLED (SSD1306)

Some boards have such display by default and should work out of the box.

For T-Beam, the preferred connection is SDA=GPIO21, SCK=GPIO22.  Some displays can directly be connected 1:1 to 3v3/GND/22/21, but note that some OLED display have connections in the order GND/VDD/SCK/SDA, in which case wiring is more difficult (swap GND/VDD).

Auto-configuration should usually work

## OLED (SH1106)

Works similarly to SSD1306. If same wiring is used, most likely autoconfig is set to SSD1306 and must be manually changed to SH1106.

## ILI 9225

Preferred connection on T-Beam 0.7 is SDA=4, CLK=21, RST=22, RS=2, CS=0
Note: This is identical to the config used by https://skp.wodzislaw.pl/wp-content/uploads/2019/03/sch_tft_tbeam.png

Preferred connection on T-Beam 1.0 and 1.1 is SDA=4, SCL=13, RST=14, RS=2, CS=0
Note: THis is DIFFERENT to the axp tgt wiring on skp.wodzislaw.pl

## ILI 9341
(Only on very recent software versions after 2020-08-06)

Can be used similarily to ILI 9225. Display type must manually be configured in the settings.

Recommended wiring is identical to ILI9225. With labels on my test display, for T-Beam 1.0/1.1:
CS=0, RESET=14, DC=2, SDI(MOSI)=4, SCK=13, SDO(MISO) is not connected

VDD and LED is wired to 3.3V; for boards supporting 5V and 3.3V operation, the jumper for disabling the voltage regulator on the display needs to be set.
