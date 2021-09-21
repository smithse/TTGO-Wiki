# SondeHub settings

## SondeHub reporting (sondehub.active)
 (default value 0, set to 1 to enable SondeHub uploading)

## SondeHub location reporting (sondehub.chase)
0: no position information is sent to SondeHub (receiver not visible on sondehub.org)
1: fixed position (from general configuration) is sent to SondeHub
2: TTGO GPS position is sent to SondeHub, chase mode is activated
3: If no GPS position is available or if GPS position is close to fixed position, then operation is identical to mode (1). Otherwise, chasemode will automatically activated, operating as in mode (2)

## sondehub.host
(default value api.v2.sondehub.org, do not change)

## Callsign (sondehub.callsign)

(default value CHANGEME_RDZTTGO, set to your station name/callsign)

## Antenna (sondehub.antenna)
(list antenna used with station on public map)

## SondeHub email (sondehub.email)
(email only visible to SondeHub developers for debugging)
