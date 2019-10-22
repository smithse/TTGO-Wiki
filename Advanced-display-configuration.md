By modified screens.txt you can change the layout of the display content (if you are using the IDE, you can change the file in RX_FSK/data and use Tools > ESP Sketch Data Upload to update the file on the board; otherwise you can use [http://rdzsonde.local/edit.html?screens.txt](http://rdzsonde.local/edit.html?screens.txt))

The file contains some self-description, but has a rather complex syntax. Maybe someday I will replace it with something nicer such as a JSON document... but not a priority right now.

**WARNING: The file parser is not tolerating wrong syntax. If you change things in a way the board does not expect, you can completely break everything, requireing re-flashing the full software image.**

# Display blocks

The file contains **display blocks** consisting of multiple lines
* Starting with a line "**@somename**"
* Several lines of "aaa=bbb"
* and finally an empty line

If "aaa" is a simple word, it is a **control statement**.

If "aaa" is a sequence of two or three numbers (such as "4,5" or "4,5,-3"), it is a **display element**.

All lines starting with '#' will be ignored

# Events

Some of the control statements (timer, key1action, key2action, timeaction) define events. Events describe transitions to a different display, or a receiver reconfiguration (switching to a different frequency). There are 11 different events
* timer: three arguments: Timer, RX Timer, No RX Timer: values in milliseconds. If some period of time is over, or if a valid signal as been received long enough, or if no valid signal has been received long enough, some action can be triggered.
* timeaction: describes what happens if a timer expires (one action for each of the three timers)
* keyNactions: describes actions if a key is pressed once, double-pressed, pressed for a medium time span, or for a long tim.

Actions are
* W: activate WiFi scan
* F: activate frequency spectrum display
* O: active "Scan" display (defined in the Config tab / config.txt: first entry in "Display" config)
* (n): activate display block number n
* &gt;: activate the next dispaly block
* D: activate the default display block (defined in the Config tab / config.txt: second entry in "Display" config)
* +: switch to the next frequency
* #: no action

The default scan display block (first block) contains
```
timer=-1,0,0
key1action=D,#,F,W
key2action=#,#,#,#
timeaction=#,D,+
```
This means:
* Timer: **-1**,0,0: no simple timer is used
* Timer: -1,**0**,0; RX timer=0: if a signal was received for more than 0 seconds (i.e. one decode iterate), trigger action 'D' (switch to default display block)
* Timer: -1,0,**0**: no RX timer=0: if no signal was received for more than 0 seconds (i.e., one decode iteration), trigger action '+' (switch to next frequency)
* Key1action: **D**,#,F,W:  If Button1 is pressed once, activate default display block
* Key1action: D,**#**,F,W: If Button1 is pressed twice, nothing happens (#)
* Key1action: D,#,**F**,W: If Button1 is pressed ~3s, activate frequency scanner
* Key1action: D,#,F,**W**: If Button1 is pressed >5s, activate WiFi scanner
* key2action: #,#,#,#: Key is not used for anything (#)

# Other control statements
* **fonts=x,y** can be used to change the font (small and large) used in **all subsequent display elements**. See comments in display.txt for currently supported fonts (depending on display)
* **color=f,b** is ignored for OLED display, and can be used to change foreground and background color for ILI9225 TFT display of all subsequent display elements (6 digit hex colour, FFFFFF is white, 000000 is black, FF0000 is red etc.). As in HTML colours, but without '#'.
* **scale=ys,xs** is ignored for OLED display. For OLED display, position are defined by line and column (lines 0..7, columns 0..15). On the TFT ILI9225 display, text can be placed arbitrarily in pixel coordinates. For compatibility with screen definitions for the OLED display, by default the TFT display also uses 8 lines and 16 columns. Lines are transformed into pixels by *22, columns into pixels by *13). If you want to directly position text in the TFT display in pixel coordiantes, you can use "scale=1,1". (In this case, your screens.txt will no longer work on OLED displays).
Alternatively, you can use fractional numbers (e.g. line 3.5) to position entries arbitrarily on the OLED display.

# Display elements
For the OLED display, display elements are defined by "line,column=something". This means that something is shown on the display at the specified position. Something has a fixed length, so on each update, the next text will completely overwrite the previous text.

For the TFT display, you can either use fixed size fonts (0,1,2) or proportional fonts. Usually the proportional fonts a nicer, but on a screen update, if a shorter text replaces a longer text, the end of the longer text will still remain on the screen. To avoid this problem, you can define the total length of some text field by using "line,column,length=something".  Length is scaled in the same way as the column (according to scale definition).

If you use "line,column,-length=somethign", something will be written right-justified in the box defined by line, column and length.

See screens.txt for details about all possible display elements.