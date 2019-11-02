# Receiver calibration and bandwidth configuration

## Calibration

In the Config tab, you can set "Show AFC value (showafc)" to 1. During reception of a RS41 or DFM sonde, the RX chip will automatically determine the frequency error, which will be shown on the display.

If your display shows a significant display error (in particular if you see a similar error for multiple sondes), the local oscillator frequency is wrong.  In this case you can enter in the config tab under "RX frequency offset (freqofs)" a correction value (in Hz).  For example, if your reception display shows "-2.5k", you should enter "-2500" as frequency offset.

## Bandwidth

Ebenso kann in der Config die Empfangsbandbreite eingestellt werden. Dazu gibt es zwei Werte: "RX AGC bandwidth (rs41.agcbw)" und "RX RX bandwidth (rs41.rxbw), beides in Hz.

Um das zu verstehen, muss man die Funktionsweise des RX-Chips kennen:
- Solange kein Signal empfangen wird, wird der Wert von AGCBW verwendet. Sobald eine Präambel empfangen wird, wird die AGC automatisch eingestellt und der Frequenzfehler gemessen (das ist auch der oben angezeigte Wert), und die RX-Frequenz automatisch korrigiert.
- Dann wird für den Rest des Empfangs des Datenpakets automatisch auf die RXBW umgeschaltet.
Das heißt, RXBW sollte so gewählt sein, wie die Bandbreite des Sondensignals. AGXBW sollte als Bandbreite des Sondensignals + maximale Frequenzabweichung, in der ein Signal noch empfangen werden soll gesetzt werden. (Chip-Doku: "The sum of the frequency offset and the 20 dB signal bandwidth must be lower than the base band filter bandwidth" )

Wichtig dabei ist, dass nur bestimmte Werte (Angabe in Hz!) unterstützt werden. Zu kleine (<2600) oder zu große (>250000) werden einfach ignoriert (Fehlermeldung nur auf serieller Konsole). Alle andere Werte werden auf den nächst größeren vom Chip unterstützen Wert aufgerundet: 2600, 3100, 3900, 5200, 6300, 7800, 10400, 12500, 15600, 20800, 25000, usw.

Standardwert in früheren Versionen ist AGCBW 25000, RXBW 12500. Durch Verkleinerung sollte sich die Empfindlichkeit verbessern lassen, eine Halbierung wohl etwa 3dB. Neue Werte werden erst bei einem Frequenzwechsel aktiv. Wer also Lust zum Testen hat, gerne :-)

