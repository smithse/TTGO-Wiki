## Over-the-air updates

If your board is connected to a WiFi access point (i.e. WiFi client mode, not access point mode), you can do an over-the-air update to the most recent version of either master or devel branch. Simply access

[http://rdzsonde.local/update.html](http://rdzsonde.local/update.html)

This will update only the software, not the file system. In some version updates, the file system content changes, and then some things might not work as expected. In these cases you need to do a full version upgrade via USB.


## File editor

http://rdzsonde.local/edit.html?file=<filename>

You can edit any small text file on the Flash file system. **Be aware that by doing unexpected modification, you can completely break the system, requiring re-flashing the system to a stable state.**
* config.txt _stores all options in the Config tab, better edit this file via the web interface_
* qrg.txt _stores all entries in the QRG tab, better edit this file via the web interface_
* networks.txt _stores all entries in the WiFi tab, better edit this file via the web interface_
* index.html _the main page of the web interface_
* style.css _the style file of the main page of the web interface_
* screens1.txt, screens2.txt, screens3.txt _the display layout configuration, see [[Advanced display configuration]] for details_

If you want to keep some part of the configuration during a full system upgrade, you can access the file via above URL, copy the file content, re-flash your board, and replace the newly flashed configuration with the copied content.