Wähle auf der Weboberfläche die Registerkarte **Config**. Wenn die automatische Konfiguration die richtigen I/O-Pins nicht automatisch auswählt, kann man hier einige Hardwareeinstellungen vornehmen (das Ändern dieser Einstellungen erfordert einen Neustart des Boards nach dem Speichern der Konfiguration):

* Anzeige:
  * Display Type: 0 für das integrierte 0,9"-OLED SSD1306 (oder extern an T-Beam angeschlossen), 2 für ein 1,3"-OLED, das wie das 0,9"-OLED angeschlossen wird, oder 1 für ein ILI9225-basierte TFT-Display
  * Konfiguriere OLED SDA und OLED SCL (und auch OLED RST, wenn eine Reset-Leitung an das Display angeschlossen ist) für ein 0,9"/1,3"-OLED-Display
  * Konfiguriere TFT SDA, TFT CLK, TFT RST, TFT CS und TFT RS für das SPI-basierte ILI9225-TFT-Display
  * Wenn das TFT-Display einen LED-Pin am Anschluss hat, verbinde diesen mit VCC
* Tasten:
  * Es werden bis zu zwei Tasten unterstützt, es müssen die GPIO-Nummern der Pins eingeben. Wenn das Board über eine echten Taster verfügt, wird dieser Taster automatisch konfiguriert. Man kann zusätzliche Tasten hinzufügen, entweder "echte" Tasten, oder den Touch-Button-Modus vom ESP32 verwenden (bei dem man nur ein Stück Draht an einen Pin anschließen und dann diesen Pin berühren muss).
  * Für echte Tasten muss die Taste zwischen Pin und GND angeschlossen werden. Der interne Pull-up-Widerstand des ESP32 wird aktiviert, sofern dies von der Hardware unterstützt wird (d. h. für GPIO < 33). Für andere Eingangspins muss man manuell einen Pull-Up-Widerstand zwischen Pin und 3V3 anschließen.
  * Im Touch-Modus muss man möglicherweise den Schwellenwert ändern. Wenn man den Schwellenwert auf 0 setzt und das Board neu starten, wird eine Kalibrierungsanzeige dargestellt. Stelle den Schwellenwert auf etwa 10-15 unter den auf dem Kalibrierungsdisplay ohne die Eingangsstifte zu berühren angezeigten Wert ein (niedrigerer Wert = weniger empfindlich; höherer Wert = empfindlicher).
* Power control:
  * Der konfigurierte GPIO-Pin wird als Ausgang konfiguriert und auf LOW geschaltet (128 zur Pin-Nummer für HIGH addieren). Nützlich für Heltec v2-Boards, die GPIO21 verwenden, um VCC des Displays einzuschalten.
* GPS:
  * Wenn ein GPS-Empfänger auf dem Board vorhaben ist (enthalten bei einen T-Beam oder extern hinzugefügt), kann rdzTTGOsonde die Entfernung und Richtung von Ihrer aktuellen Position zur empfangenen Sonde berechnen. Man muss konfigurieren, mit welchem ​​RXD-Pin der GPS-Chip verbunden ist. Die Software erwartet NMEA-Daten (RMC-Datensätze) mit 9600 Baud, 8N1. Es werden derzeit keine Daten zum GPS-Chip übertragen, der TXD-Pin sollte daher auf -1 eingestellt werden.
