## Using the ttgoconfig python script ##

### With USB serial connection

* python3 scrpits/ttgoconfig update develXXX.bin  (or masterYYY.bin)

  Fetches the file https://github.com/dl9rdz/rdz_ttgo_sonde/blob/gh-pages/devel/develXXX.bin?raw=true, which is the same firmware image as on http://rdzsonde.mooo.com/download.html, and flashes it to the TTGO board (depends on the auto detection of the right serial port by esptool)

* python3 scripts/ttgoconfig backup XYZ.bin

  Reads the current firmware image from the TTGO board (starting at 0x1000, size 0x3FF000) and saves it as XYZ.bin

* python3 scripts/ttgoconfig restore XYZ.bin

  Flashes the file XYZ.bin to the TTGO board (at offset 0x1000). This works with images created with backup, and also with images downloaded manually from rdzsonde.mooo.com

### With WiFi connection to TTGO board

For all commands below, you can use "--ttgo=IP" to specify the IP address. By default, "rdzsonde.local" is used. This works only if your host system supports mDNS discovery (tested on MacOS only).

For all commands below, you can use "--dir=XYZ" to save/read files from the folder XYZ. For get commands, you can use "--print" to show the file content on screen instead of saving it to a file.

* python3 scripts/ttgoconfig get file XYZ

  Reads file XYZ from the TTGO file system and saves it locally (see --print / --dir=xxx above)

* python3 scripts/ttgoconfig put file XYZ

  Writes file XYZ to the TTGO file system

* python3 scripts/ttgoconfig get <all|config|qrg|networks|screens>

  Short convenience form for get file. all=all standard files, screens=all screensX.txt files, qrg=qrg.txt, networks=networks.txt

* python3 scripts/ttgoconfig put <all|config|qrg|networks|screens>

  See get...