# Receiver calibration and bandwidth configuration

## Calibration

During reception of a RS41, tentatively also on M10/M20, the RX chip will automatically determine the frequency error, which will be shown on the display.  For other sonde types, some value will be shown as well, but it might be less accurate, as only RS41 uses the chip's AFC feature directly.  So if possible, use a RS41 for calibration.

If your display shows a significant display error (in particular if you see a similar error for multiple sondes), the local oscillator frequency is wrong.  In this case you can enter in the config tab under "RX frequency offset (freqofs)" a correction value (in Hz).  For example, if your reception display shows "-2.5k", you should enter "-2500" as frequency offset.

## Bandwidth

You can also use the Config tab to adjust the receiver bandpass filter. There are two values: "RX AGC bandwidth (rs41.agcbw)" und "RX RX bandwidth (rs41.rxbw)". Both entries are values in Hz.

To understand how this works you need to understand the basic functionality of the RX chip (SX127x):
- As long as no signal is received, the value of AGCBW is used. As soon as a preamble is detected, the input gain is automatically adjusted, the frequency error is measured (this is the value shown above as frequency offset), and the frequency is corrected automatically.
- During the reception of the following data packet, the bandwidth is set to the RXBW value.
This means that RXBW should be set such that it matches the bandwidth of the RF signal of the sonde. AGCBW should be set to RXBW plus the maximum frequency error for which a signal should still be decoded. (SX127x documentation: "The sum of the frequency offset and the 20 dB signal bandwidth must be lower than the base band filter bandwidth" )

It is imporant to known that only some discrete values (in Hz) are supported. Values that are too low (<2600) or too large (>250000) will simply be ignored (error message only on serial console). All other values are rounded UP to the next supported value: 2600, 3100, 3900, 5200, 6300, 7800, 10400, 12500, 15600, 20800, 25000, usw.

Default values used to be AGCBW 25000, RXBW 12500. By reducing the bandwidth, you can enhance sensitivity (approximately half of the bandwidth is 3dB more sensitive). Alterations in the config tab will only be activated after a frequency change.

Note that the automated frequency measurement and correction is only well supported for RS41. For these sondes, the chip is pretty tolerant to frequency offsets.  However, RS92 and M10 are different (they do not have a preamble that is directly supported by SX1278).  A manual frequency offset correction (measured with RS41) is essential for good sensitivity for those signals.
