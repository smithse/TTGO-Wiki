# SondeHub frequency import

The configuration in the QRG tab can be automatically modified with information from SondeHub.
This feature works only if the configuration of static receiver position (in General configuration) or a valid GPS position from the TTGO-internal GPS are available.

## SondeHub frequency import active (sondehub.fiactive)
0=disabled, 1=active

## Import frequency (sondehub.fiinterval)
Interval, in minutes, how often a request is sent to SondeHub. Minimum 5 minutes. 

## Import maximum distance (sondehub.fimaxdist)
Distance passed to SondeHub in the request, in order to query the data base for information.

## Import maximum age (sondehub.fimaxage)
Time parameter passed to SondeHub in the request, in order to query data from the data base not older than this maximum value.