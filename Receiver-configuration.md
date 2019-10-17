# Receiver calibration and bandwidth configuration

## Calibration

In der Config kann "Show AFC value (showafc)" auf 1 gesetzt werden, dann wird beim Empfang einer Sonde der vom RX-Chip ermittelte Frequenzoffset angezeigt.
Wenn hier bei mehreren Sonden immer ein ähnlicher Fehler steht, ist wohl die lokale Oszillatorfrequenz des Empfängers falsch. Hier kann man in der Config "RX frequency offset (freqofs)" einen Korrekturwert (in Hz) eintragen. (vermutlich wäre ein ppm-Wert theoretisch sinnvoller, aber fürs erste fand ich einen festen Offset intuitiver zum eintragen, und der Unterschied sollte zu vernachlässigen sein ;-))

## Bandwidth

Ebenso kann in der Config die Empfangsbandbreite eingestellt werden. Dazu gibt es zwei Werte: "RX AGC bandwidth (rs41.agcbw)" und "RX RX bandwidth (rs41.rxbw), beides in Hz.

Um das zu verstehen, muss man die Funktionsweise des RX-Chips kennen:
- Solange kein Signal empfangen wird, wird der Wert von AGCBW verwendet. Sobald eine Präambel empfangen wird, wird die AGC automatisch eingestellt und der Frequenzfehler gemessen (das ist auch der oben angezeigte Wert), und die RX-Frequenz automatisch korrigiert.
- Dann wird für den Rest des Empfangs des Datenpakets automatisch auf die RXBW umgeschaltet.
Das heißt, RXBW sollte so gewählt sein, wie die Bandbreite des Sondensignals. AGXBW sollte als Bandbreite des Sondensignals + maximale Frequenzabweichung, in der ein Signal noch empfangen werden soll gesetzt werden. (Chip-Doku: "The sum of the frequency offset and the 20 dB signal bandwidth must be lower than the base band filter bandwidth" )

Wichtig dabei ist, dass nur bestimmte Werte (Angabe in Hz!) unterstützt werden. Zu kleine (<2600) oder zu große (>250000) werden einfach ignoriert (Fehlermeldung nur auf serieller Konsole). Alle andere Werte werden auf den nächst größeren vom Chip unterstützen Wert aufgerundet: 2600, 3100, 3900, 5200, 6300, 7800, 10400, 12500, 15600, 20800, 25000, usw.

Standardwert in früheren Versionen ist AGCBW 25000, RXBW 12500. Durch Verkleinerung sollte sich die Empfindlichkeit verbessern lassen, eine Halbierung wohl etwa 3dB. Neue Werte werden erst bei einem Frequenzwechsel aktiv. Wer also Lust zum Testen hat, gerne :-)

