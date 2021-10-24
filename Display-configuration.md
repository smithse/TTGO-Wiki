# OLED/TFT display configuration

## Screen config (0=automatic, 1-5=predefined, other=custom).
Selects the screen layout file to be used (value X selects file screensX.txt).

Value 0 makes an automated selection (which usually is what you want to use) based on other configuration parameters:
* Display type OLED (SSD1306 or SH1106): screens1.txt
* Display type ILI9225: Orientation 1 or 3 (landscape): screens2.txt, otherweise (portrait) screens3.txt
* Display type ILI9341/9342: Orientation 1 or 3 (landscape): screens4.txt, otherwise (portrait) [screens5.txt](screens5.txt)

Make sure to select a screens file that fits to your hardware config.
Other custom screen files can be created, uploaded, and selected here.

(Selecting a different screen config probably requires rebooting the TTGO.)

## Display screens
Defines which screens from the screen layout file (screensX.txt) should be used. On the left, all entries from the screens#.txt file are shown. Enter a list of numbers. The first number should be a "Scan" layout. After that, you can put a sequence of numbers corresponding to screens you can cycle through with a button.

## No-RX-timeout
If set to -1, a decoder display will remain active forever even if no signal is received anymore. Any other value X will trigger the No-RX action of the TTGO after X seconds of no reception (in the default screen, this is the "0"-action, which causes the TTGO to switch back to Scan mode).

Technically, any letter "N" in the screens#.txt files will be replaced by the No-RX-timeout value when the file is read. This means that any change to this parameter will only have effect after the file is read again (for example, after a reset). 

## TFT orientation
You can use this value to rotate the TFT display (0=portrait, 1=landscape, 2=portrait rotated 180°, 3=landscape rotated 180°.
For the OLED display, 0,1,2 all mean "normal", 3 means "rotated 180°". 90° rotation is not supported on the OLED display.
