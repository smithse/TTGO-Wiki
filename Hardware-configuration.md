
On the web interface, select the **Config** tab. If autoconfiguration does not select the right I/O pins automatically, you can adjust some hardware settings here (at the bottom of the page; changing these settings require restarting the board after saving the configuration):

* Display: 
  * Display type: 0 for the on-board SSD1306 0.9" OLED (or externally connected to T-Beam), 2 for the 1.3" OLED connected the same way as the 0.9", or 1 for the ILI9225-based TFT display
  * Configure OLED SDA and OLED SCL (and also OLED RST if a reset line is connected to your display) for the 0.9"/1.3" OLED displays
  * Configure TFT SDA, TFT CLK, TFT RST, TFT CS and TFT RS for SPI-based ILI9225 TFT display
* Buttons:
  * Up to two buttons are supported, you have to enter the GPIO number of the pins. If your supported board comes with an physical button, this button is automatically configured. You can add additional buttons, either "real" buttons, or use the touch button mode of ESP32 (in which you just connect a piece of wire to a pin and then just touch that pin). 
  * In touch mode, you might have to change the threshold value. Calibration currently is simply by trial and error.
* GPS:
  * If you have a GPS receiver on your board (on-board for a T-Beam, or external), rdzTTGOsonde can calculate distance and bearing from your current position to the received sonde. You have to configure which RXD pin the GPS is connected to.
