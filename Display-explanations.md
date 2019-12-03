# 01-Legacy

<img src="https://github.com/dl9rdz/rdz_ttgo_sonde/wiki/images/01-Legacy.jpg" width="300px"/>

|Nr | Content |
|---|---|
| 1 | Sonde type |
| 2 | Sonde ID |
| 3 | Latitude |
| 4 | Longitude |
| 5 | RSSI (signal strength) |
| 6 | Sonde frequency |
| 7 | Altitude |
| 8 | Horizontal speed |
| 9 | Vertical speed |
| 10 | Reception status of last 18 frames: <br> \|=ok, .=no rx (no frame start detected within about 1s), <br>E=rx with error (depending on sonde: crc error, rs decoding error, etc.) |

# 02-Field

<img src="https://github.com/dl9rdz/rdz_ttgo_sonde/wiki/images/02-Field.jpg" width="300px"/>

|Nr | Content |
|---|---|
| 1 | Sonde ID |
| 2 | Latitude |
| 3 | Longitude |
| 4 | Altitude |
| 5 | Horizontal speed |
| 6 | Vertical speed |
| 7 | Reception status of last 18 frames: <br> \|=ok, .=no rx (no frame start detected within about 1s), <br>E=rx with error (depending on sonde: crc error, rs decoding error, etc.) |

# 03-Field2

<img src="https://github.com/dl9rdz/rdz_ttgo_sonde/wiki/images/03-Field2.jpg" width="300px"/>

|Nr | Content |
|---|---|
| 1 | Sonde ID |
| 2 | Latitude |
| 3 | Longitude |
| 4 | Altitude |
| 5 | Sonde frequency |
| 6 | Sonde type |
| 7 | Horizontal speed |
| 8 | Vertical speed |
| 9 | Reception status of last 18 frames: <br> \|=ok, .=no rx (no frame start detected within about 1s), <br>E=rx with error (depending on sonde: crc error, rs decoding error, etc.) |

# 04-GPSDisp

<img src="https://github.com/dl9rdz/rdz_ttgo_sonde/wiki/images/04-GPSDist.jpg" width="300px"/>

|Nr | Content |
|---|---|
| 1 | Sonde ID |
| 2 | Latitude |
| 3 | Longitude |
| 4 | Symbol on the left if TTGO GPS fix; d=xxx: distance to sonde |
| 5 | Sonde frequency |
| 6 | Sonde type |
| 7 | Altitude |
| 8 | Horizontal speed |
| 9 | Vertical speed |
|10 | Course over ground (COG) of TTGO, <br> Bearing (difference between COG and direction to sonde) <br> 0=moving towards sonde
|11 | Reception status of last 18 frames: <br> \|=ok, .=no rx (no frame start detected within about 1s), <br>E=rx with error (depending on sonde: crc error, rs decoding error, etc.) |
|12 | Direction to sonde (0=north, 90=east, 180=south, 270=west) |

