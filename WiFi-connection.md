Some notes on accessing the TTGO WiFi, in particular on Android:

Basic background: WiFi can operate in station mode (connected to an access point) or access point mode (allowing other devices to connect to it), see [[General Configuration]]

If you use the access point mode in combination with Android phones, you may run into problems:
* If, on an Android phone, you have mobile data enabled and connect to the TTGO (in access point mode), your phone tries to be "smart", it will detect that there is no Internet connectivity via the access point, so very likely it will route network traffic via mobile data instead of via WiFi. In this case, you will NOT be able to access the TTGO (using the IP shown on the TTGO, or using MDSN discovery, or using the rdzwx-go App)
* First fix for this problem: Disable mobile data on your phone. Then all network traffic will go to the WiFi interface.
* Then you can access the TTGO on your phone (using the default IP: http://192.168.4.1/, or using the Android App rdzwx-go)
* A better solution is to use your phone as hotspot, and connect the TTGO to that AP. Use the previous steps to access the TTGO configuration, add a hotspot name/password, then reconfigure your phone to enable the hotspot, and restart the TTGO (it will connect to the hotspot)
* The TTGO now will have a different IP address (shown on the display). Use `http://<new IP>/`. http://rdzsonde.local/ will always work instead of using an IP address (if your system / browser supports MDNS lookup). 

Additional hints:
* For using the rdzwx-go app, "Kiss TNC" must be enabled in the config (it is enabled in the default config, just don't disable it)
* MDNS (i.e. accessing the TTGO using http://rdzsonde.local) should work on most browsers on PCs (any OS), on iOS, and on Android starting version 12. It is NOT supported directly on Android 11 and below, i.e. this will NOT work in your browser. The Android app rdzwx-go contains code to do MDNS lookups on older Android version and will automatically find the IP address of your TTGO (on the local network).