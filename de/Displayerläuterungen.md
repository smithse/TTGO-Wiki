# 01-Legacy

<img src="https://github.com/dl9rdz/rdz_ttgo_sonde/wiki/images/01-Legacy.jpg" width="300px"/>

|Nr | Content |
|---|---|
| 1 | Sondentyp |
| 2 | Sonden-ID |
| 3 | Breitengrad |
| 4 | Längengrad |
| 5 | RSSI (Signalstärke) |
| 6 | Sondenfrequenz |
| 7 | Höhe |
| 8 | Horizontalgeschwindigkeit |
| 9 | Vertikalgeschwindigkeit |
| 10 | Empfangsstatus der letzten 18 Pakete: <br> \|=ok, .=nicht ok (kein Framestart erkannt innerhalb ca. 1s)<br>E=rx mit Fehler (je nach Sonde: CRC-Fehler, RS-Decoding-Fehler, etc.) |

# 02-Field

<img src="https://github.com/dl9rdz/rdz_ttgo_sonde/wiki/images/02-Field.jpg" width="300px"/>

|Nr | Content |
|---|---|
| 1 | Sonden-ID |
| 2 | Breitengrad |
| 3 | Längengrad |
| 4 | Höhe |
| 5 | Horizontalgeschwindigkeit |
| 6 | Vertikalgeschwindigkeit |
| 7 | Empfangsstatus der letzten 18 Pakete: <br> \|=ok, .=nicht ok (kein Framestart erkannt innerhalb ca. 1s)<br>E=rx mit Fehler (je nach Sonde: CRC-Fehler, RS-Decoding-Fehler, etc.) |

# 03-Field2

<img src="https://github.com/dl9rdz/rdz_ttgo_sonde/wiki/images/03-Field2.jpg" width="300px"/>

|Nr | Content |
|---|---|
| 1 | Sonden-ID |
| 2 | Breitengrad |
| 3 | Längengrad |
| 4 | Höhe |
| 5 | Sondenfrequenz |
| 6 | Sondentyp |
| 7 | Horizontalgeschwindigkeit |
| 8 | Vertikalgeschwindigkeit |
| 9 | Empfangsstatus der letzten 18 Pakete: <br> \|=ok, .=nicht ok (kein Framestart erkannt innerhalb ca. 1s)<br>E=rx mit Fehler (je nach Sonde: CRC-Fehler, RS-Decoding-Fehler, etc.) |

# 04-GPSDisp

<img src="https://github.com/dl9rdz/rdz_ttgo_sonde/wiki/images/04-GPSDist.jpg" width="300px"/>

|Nr | Content |
|---|---|
| 1 | Sonden-ID |
| 2 | Breitengrad |
| 3 | Längengrad |
| 4 | Symbol on the left if TTGO GPS fix; d=xxx: distance to sonde |
| 5 | Sondenfrequenz |
| 6 | Sondentyp |
| 7 | Höhe |
| 8 | Horizontalgeschwindigkeit |
| 9 | Vertikalgeschwindigkeit |
|10 | Course over ground (COG) vom TTGO, <br> Bearing (Winkeldifferenz zwischen COG und Richtung zur Sonde)<br> 0=man bewegt sich Richtung Sonde
|11 | Empfangsstatus der letzten 18 Pakete: <br> \|=ok, .=nicht ok (kein Framestart erkannt innerhalb ca. 1s)<br>E=rx mit Fehler (je nach Sonde: CRC-Fehler, RS-Decoding-Fehler, etc.) |
|12 | Richtung zur Sonde (0=north, 90=east, 180=south, 270=west) |

