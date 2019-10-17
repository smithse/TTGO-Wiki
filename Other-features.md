## Over-the-air updates

If your board is connected to a WiFi access point (i.e. WiFi client mode, not access point mode), you can do an over-the-air update to the most recent version of either master or devel branch. Simply access

[http://rdzsonde.local/update.html](http://rdzsonde.local/update.html)

This will update only the software, not the file system. In some version updates, the file system content changes, and then some things might not work as expected. In these cases you need to do a full version upgrade via USB.


## File editor

http://rdzsonde.local/edit.html?filename

You can edit any small text file on the Flash file system. **Be aware that by doing unexpected modification, you can completely break the system, requiring re-flashing the system to a stable state.**
* config.txt _stores all options in the Config tab, better edit this file via the web interface_
* qrg.txt _stores all entries in the QRG tab, better edit this file via the web interface_
* networks.txt _stores all entries in the WiFi tab, better edit this file via the web interface_
* index.html _the main page of the web interface_
* style.css _the style file of the main page of the web interface_
* screens.txt _the display layout configuration, see below for details_