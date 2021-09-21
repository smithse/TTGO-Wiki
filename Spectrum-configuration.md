
# Spectrum display configuration

## ShowSpectrum (s) (``spectrum``)
If set to a value spectrum >= 0, the spectrum mode is started after reboot (otherwise, the scan mode).
If spectrum > 0, the spectrum display will be active only for ``spectrum`` seconds and then automatically switch to scan mode
Set to -1 to disable spectrum display

## Startfreq (MHz) (``startfreq``)
Starting frequency in MHz, usually 400 MHz

## Bandwidth (kHz) (``channelbw``)
Configuration value for RXBW during spectrum recording (needs additional testing, probably we should (also) set AGCBW?)

## Spectrum MHz marker (``marker``)
Display MHz values (start, end) in display in spectrum mode

## Spectrum noisefloor (``noisefloor``)
RSSI value at bottom edge of display


