
On the web interface, select the **Config** tab. If autoconfiguration does not select the right I/O pins automatically, you can adjust some hardware settings here (at the bottom of the page; changing these settings require restarting the board after saving the configuration):

* Display: 
  * Display type: 0 for the on-board SSD1306 0.9" OLED (or externally connected to T-Beam), 2 for the 1.3" OLED connected the same way as the 0.9", or 1 for the ILI9225-based TFT display
  * Configure OLED SDA and OLED SCL (and also OLED RST if a reset line is connected to your display) for the 0.9"/1.3" OLED displays
  * Configure TFT SDA, TFT CLK, TFT RST, TFT CS and TFT RS for SPI-based ILI9225 TFT display
* Buttons:
  * Up to two buttons are supported, you have to enter the GPIO number of the pins. If your supported board comes with an physical button, this button is automatically configured. You can add additional buttons, either "real" buttons, or use the touch button mode of ESP32 (in which you just connect a piece of wire to a pin and then just touch that pin).
* For real buttons, you need to connect the button between pin and GND. The internal pull-up resistors of the ESP32 is activated where supported by hardware (i.e., for GPIO<33). For other input pins, you need to manually connect a pull-up resistor between pin and 3V3.
  * In touch mode, you might have to change the threshold value. If you set threshold to 0 and reboot your board, a calibration display is shown. Set the treshold to about 10-15 below the values shown on the calibration display without touching the input pins (lower value=less sensitive; higher value=more sensitive)
* Power control pin:
  * Configured GPIO pin will be configured as output and driven LOW (add 128 to pin number for HIGH). Useful for Heltec v2 boards that use GPIO21 to switch the display's VCC on.
* GPS:
  * If you have a GPS receiver on your board (on-board for a T-Beam, or external), rdzTTGOsonde can calculate distance and bearing from your current position to the received sonde. You have to configure which RXD pin the GPS is connected to. The software expects NMEA data (RMC records) at 9600 baud, 8N1