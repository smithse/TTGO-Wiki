# Empfängerkalibrierung und Bandbreitenkonfiguration

## Kalibrierung

In der Registerkarte Config können Sie "Show AFC value (showafc)" auf 1 setzen. Während des Empfangs einer RS41- oder DFM-Sonde ermittelt der RX-Chip automatisch den Frequenzfehler, der auf dem Display angezeigt wird.

Wenn Ihr Display einen signifikanten Anzeigefehler anzeigt (insbesondere, wenn Sie einen ähnlichen Fehler für mehrere Sonden sehen), ist die Frequenz des lokalen Oszillators falsch. In diesem Fall können Sie in der Registerkarte Config unter "RX Frequency Offset (Freqofs)" einen Korrekturwert (in Hz) eingeben. Wenn Ihre Empfangsanzeige beispielsweise "-2,5k" anzeigt, sollten Sie "-2500" als Frequenzversatz eingeben.

Bandbreite

Sie können auch die Registerkarte Config verwenden, um den Empfänger-Bandpassfilter anzupassen. Es gibt zwei Werte: "RX AGC-Bandbreite (rs41.agcbw)" und "RX RX-Bandbreite (rs41.rxbw)". Beide Angaben sind Werte in Hz.

Um zu verstehen, wie dies funktioniert, müssen Sie die Grundfunktionen des RX-Chips (SX127x) verstehen:
- Solange kein Signal empfangen wird, wird der Wert von AGCBW verwendet. Sobald eine Präambel erkannt wird, wird die Eingangsverstärkung automatisch angepasst, der Frequenzfehler gemessen (dies ist der oben als Frequenzversatz angegebene Wert) und die Frequenz wird automatisch korrigiert.
- Beim Empfang des folgenden Datenpakets wird die Bandbreite auf den RXBW-Wert gesetzt.
Dies bedeutet, dass RXBW so eingestellt werden sollte, dass es mit der Bandbreite des HF-Signals der Sonde übereinstimmt. AGCBW sollte auf RXBW plus dem maximalen Frequenzfehler eingestellt werden, für den ein Signal noch decodiert werden soll. (SX127x-Dokumentation: "Die Summe aus Frequenzoffset und 20-dB-Signalbandbreite muss niedriger sein als die Bandbreite des Basisbandfilters")

Es ist wichtig zu wissen, dass nur einige diskrete Werte (in Hz) unterstützt werden. Zu niedrige (<2600) oder zu große (> 250000) Werte werden einfach ignoriert (Fehlermeldung nur bei serieller Konsole). Alle anderen Werte werden auf den nächsten unterstützten Wert aufgerundet: 2600, 3100, 3900, 5200, 6300, 7800, 10400, 12500, 15600, 20800, 25000, usw.

Die Standardwerte waren früher AGCBW 25000, RXBW 12500. Durch Verringern der Bandbreite können Sie die Empfindlichkeit erhöhen (ungefähr die Hälfte der Bandbreite ist 3 dB empfindlicher). Änderungen in der Registerkarte Config werden erst nach einer Frequenzänderung aktiviert.

Beachten Sie, dass die automatische Frequenzmessung und -korrektur nur für RS41 und DFM06 / 09 aktiviert ist. Für diese Sonden ist der Chip gegenüber Frequenzversätzen ziemlich tolerant. RS92 und M10 unterscheiden sich jedoch (sie haben keine Präambel, die direkt von SX1278 unterstützt wird). Eine manuelle Frequenzversatzkorrektur (gemessen mit RS41) ist für eine gute Empfindlichkeit dieser Signale unerlässlich.
