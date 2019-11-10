**Wichtiger Hinweis (für alle Boards): _Du brauchst die 433 MHz-Version_ (der 433 MHz Empfänger wird als 403 MHz Empfänger verwendet). Die 868/915 MHz Version funktioniert nicht**

# Empfohlene Boards

## TTGO LORA v2.1_1.6

Vorteile:
- Kleines Board mit integriertem 0.96"-OLED-Display
- Hervorragende HF-Empfindlichkeit (besser als die LORA v1.0-Boards) - ein GROSSER Unterschied!
- SMA-Anschluss (einfacher, eine externe Antenne anzuschließen)

Nachteile:
- nur ein Reset-Taster, kein zweiter Taster (aber Anschlüsse des Boards können als "Touch Pins" konfiguriert werden, einfach ein Stück Draht anlöten und
durch Berühren als Taster verwenden)

## TTGO T-BEAM 1.0 (neue Version, mit Laderegler AXP192)

Vorteile:
- Auch große HF-Empfindlichkeit, genau wie auf Board weiter oben
- Integriertes GPS (ermöglicht die Anzeige von Entfernung und Richtung zur Radiosonde)
- Integrierter Batteriehalter und Laderegler (18650-Zelle)

Nachteile(?):
- Kein integriertes Display (aber wenn man ein größeres 1,3" OLED- oder 2" TFT-Display bevorzugt, ist dies eher ein Vorteil, da man ein Display in der bevorzugten Größe anschließen kann)
- Größer als andere Boards, wenn man zum v2.1-Board einen kleinen flachen LiPo hinzufügt, erhält man ein kompakteres Gerät

Bitte beachten, dass beim T-Beam 1.0 einige Pins anders verwendet werden als beim älteren T-Beam v0.7. Anleitungen, wie man zusätzliche Dinge verbindet, die man im Internet für die Version 0.7 finden, sind für die Version 1.0 möglicherweise nicht korrekt.
- Man kann ein I2C-OLED-Display wie beim alten T-Beam 0.7 an Pin 21/22 (SDA / SCL) anschließen
- Man kann SDA / SCL nicht in der Software austauschen, da SDA / SCL auch für die Kommunikation mit dem Energieverwaltungs-Chip verwendet werden
- Aus dem gleichen Grund sollte man kein SPI-Display an Pin 21/22 anschließen (manchmal gibt es so einen Vorschlag für das T-Beam 0.7).

# Zusätzliche Boards

Der Code wurde auch mit folgenden Boards getestet:

## TTGO LoRa v1.0

Erstes unterstütztes Board, funktioniert gut, aber die Empfindlichkeit des 403-MHz-Empfangs ist nicht so gut wie bei anderen Boards.  Ich habe mein Board als "Wemos® TTGO LORA SX1278 ESP322 433 MHz" von Banggood Anfang 2019 erhalten. Es scheint identisch zu dem "LILYGO TTGO LORA" zu sein, das derzeit von Banggood vertrieben wird (ungetestet).

Das Board verfügt über eine zweite Taste (zusätzlich zur Reset-Taste), mit der die Software gesteuert werden kann, und ein integriertes 0,96-Zoll-OLED-Display.

Auf dem Board befindet sich ein winziger I-PEX-Anschluss für die Antenne (man benötigt also ein Adapterkabel, um eine Antenne mit einem gängigeren SMA-Anschluss anzuschließen).

## HELTEC TTGO LoRa v1

In Bezug auf die Platinenbelegung (Pinbelegung) aus softwaretechnischer Sicht sehr ähnlich zu TTGO LoRa v1.0.

Keine Angaben zur Empfangsempfindlichkeit im Vergleich zu anderen Karten.

## HELTEC TTGO LoRa v2

Dieses Board ist dem v1.0 Board sehr ähnlich. Heltec gibt an, dass die HF-Impedanzanpassung verbessert wurde, sodass die HF-Leistung möglicherweise besser ist als bei der v1-Platine. Empfindlichkeit nicht verifiziert.

## TTGO T-BEAM (alte Version v0.7, TP5400 Ladegerät IC)

Es wird unterstützt und kann nach Hardware-Änderungen ein schönes Board sein.

Vorteile:
- GPS auf dem Board. Ermöglicht die automatische Anzeige von Entfernung / Richtung zur Sonde

Vorteile / Nachteile:
- Kein integriertes Display (siehe T-Beam 1.0)

Nachteile:
- Größer als die anderen Boards
- Inkonsistente Qualität. Mein Board hat zwei Probleme (aber anscheinend haben andere Leute etwas mehr Glück):
  * Beim Anschließen an USB (insbesondere ohne Batterie im Batteriehalter) macht die Spule des Batterieladegeräts ein sehr störendes hörbares Geräusch (anscheinend sind alle Platinen etwas von diesen Problemen betroffen, aber meines macht ein besonderes Ladegeräusch, für andere ist es nur ein wenig Lärm).
  * Der Akku-Ladegerät-Chip verursacht insbesondere im reinen Akkubetrieb GROSSE HF-Störungen. (https://vimeo.com/341131491)

Man kann das Qualitätsproblem beseitigen, indem man den Batterieladechip deaktivieren und eine Batterie direkt an die 5-V-Stromversorgung anschließen. Nach dieser Änderung kann man den Akku nicht über USB aufladen (bzw. sollten dies aus Sicherheitsgründen nicht tun).



# Schlussbemerkungen zu verschiedenen Versionen

In vielen Online-Shops können Sie die Frequenzversion als "Farbe" wählen

Die 868/915-MHz-Version enthält den SX1276-Empfängerchip. Der Chip unterstützt sowohl 433 MHz als auch 868/915 MHz, verwendet jedoch unterschiedliche Eingangspins. Das Board verbindet die Antenne mit dem 868/915-MHz-Eingangspin, der 433-MHz-Pin ist nicht verbunden. Theoretisch kann die 868/915-MHz-Version so modifiziert werden, dass sie als 403-MHz-Empfänger funktioniert, indem die Antenne direkt an den richtigen Pin des Chips angeschlossen wird. Dies erfordert jedoch etwas fortgeschrittene SMD-Lötfähigkeiten.

Also am besten sicherstellen, dass man die 433-MHz-Version des Boards erhält!
