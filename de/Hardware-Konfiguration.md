Wählen Sie auf der Weboberfläche die Registerkarte ** Config **. Wenn die automatische Konfiguration die richtigen E / A-Pins nicht automatisch auswählt, können Sie hier einige Hardwareeinstellungen vornehmen (unten auf der Seite; das Ändern dieser Einstellungen erfordert einen Neustart der Karte nach dem Speichern der Konfiguration):

* Anzeige:
  * Anzeigetyp: 0 für die integrierte 0,9-Zoll-OLED SSD1306 (oder extern an T-Beam angeschlossen), 2 für die 1,3-Zoll-OLED, die auf dieselbe Weise wie die 0,9-Zoll-OLED angeschlossen ist, oder 1 für das ILI9225-basierte TFT-Display
  * Konfigurieren Sie OLED SDA und OLED SCL (und auch OLED RST, wenn eine Reset-Leitung an Ihr Display angeschlossen ist) für die 0,9 "/ 1,3" -OLED-Displays
  * Konfigurieren Sie TFT SDA, TFT CLK, TFT RST, TFT CS und TFT RS für das SPI-basierte ILI9225-TFT-Display
* Tasten:
  * Es werden bis zu zwei Tasten unterstützt, Sie müssen die GPIO-Nummer der Pins eingeben. Wenn Ihr unterstütztes Board über eine physische Schaltfläche verfügt, wird diese Schaltfläche automatisch konfiguriert. Sie können zusätzliche Tasten hinzufügen, entweder "echte" Tasten, oder den Touch-Button-Modus von ESP32 verwenden (bei dem Sie nur ein Stück Draht an einen Pin anschließen und dann diesen Pin berühren).
  * Für echte Tasten müssen Sie die Taste zwischen Pin und GND verbinden. Der interne Pull-up-Widerstand des ESP32 wird aktiviert, sofern dies von der Hardware unterstützt wird (d. H. Für GPIO <33). Für andere Eingangspins müssen Sie manuell einen Pull-Up-Widerstand zwischen Pin und 3V3 anschließen.
  * Im Touch-Modus müssen Sie möglicherweise den Schwellenwert ändern. Wenn Sie den Schwellenwert auf 0 setzen und Ihr Board neu starten, wird eine Kalibrierungsanzeige angezeigt. Stellen Sie den Schwellenwert auf etwa 10-15 unter den auf dem Kalibrierungsdisplay angezeigten Werten ein, ohne die Eingangsstifte zu berühren (niedrigerer Wert = weniger empfindlich; höherer Wert = empfindlicher).
* Stromsteuerungsstift:
  * Der konfigurierte GPIO-Pin wird als Ausgang konfiguriert und auf LOW geschaltet (128 zur Pin-Nummer für HIGH addieren). Nützlich für Heltec v2-Boards, die GPIO21 verwenden, um die VCC des Displays einzuschalten.
* GEOGRAPHISCHES POSITIONIERUNGS SYSTEM:
  * Wenn Sie einen GPS-Empfänger auf Ihrem Board haben (an Bord für einen T-Beam oder extern), kann rdzTTGOsonde die Entfernung und Peilung von Ihrer aktuellen Position zur empfangenen Sonde berechnen. Sie müssen konfigurieren, mit welchem ​​RXD-Pin das GPS verbunden ist. Die Software erwartet NMEA-Daten (RMC-Datensätze) mit 9600 Baud, 8N1
