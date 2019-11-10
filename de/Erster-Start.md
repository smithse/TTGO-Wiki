## Erster Start (Autokonfiguration)

Die Software wird versuchen, den verwendeten Board-Typ automatisch zu erkennen (basierend auf dem Status einiger Eingabepins während des Startvorgangs). Wenn man ein anderes Board, zusätzliche an das Board angeschlossene Dinge oder eine andere Verkabelung eines externen Displays verwendet, funktioniert dies möglicherweise nicht (die automatische Konfiguration sollte in der Standardkonfiguration aller in [[Unterstützte Boards]] genannten Geräte funktionieren).

* TTGO Lora32 v1 / Heltec v1 / Heltec v2: (wird beim Start durch GPIO16 == 0 erkannt)
  * 0,9" OLED-Display angeschlossen an SDA = 4, SCL = 15 (RST = 16)
  * Taste1 an GPIO0, Taste2 als Touch-Sensor an GPIO13
  * LED an GPIO2 (möglicherweise GPIO25 bei den Heltec-Boards?)
* TTGO Lora32 v2.1: (wird beim Start durch GPIO17 == 1 erkannt)
  * 0,9" OLED-Display an SDA = 21, SCL = 22 (RST = 16) angeschlossen
  * Taste1 als Touch-Sensor an GPIO2, Taste2 als Touch-Sensor an GPIO14
  * LED an GPIO25
* TTGO T-Beam v0.7: (durch GPIO12 == 1 beim Start erkannt)
  * Taste1 an GPIO39, Taste2 als Touch-Input an GPIO13
  * GPS RXD an GPIO12
  * (a) 0,9"/1,3" OLED-Display an SDA = 21, SCL = 22 (RST = 16) angeschlossen (wenn GPIO21 == 1)
  * (b) SPI-TFT-Display angeschlossen an SDA = 4, CLK = 21, RST = 22, RS = 2, CS = 0 (wenn GPIO21 == 0)
* TTGO T-Beam v1.0: (ansonsten)
  * Button1 an GPIO38, Button2 als Touch-Sensor an GPIO15
  * GPS RXD an GPIO34
  * Power Management Controller an SDA = 21, SCL = 22
  * (a) 0,9"/ 1,3"-OLED-Anzeige, verbunden mit SDA = 21, SCL = 22 (RST = 16) (durch I2C-Bus-Probe)
  * (b) An SDA = 4 angeschlossenes SPI-TFT-Display, CLK = 13, RST = 14, RS = 2, CS = 0

## Erste Konfiguration

Nach dem Einschalten erstellt das Gerät einen WLAN-Zugangspunkt mit der SSID **RDZsonde** und dem Kennwort **RDZsonde**.
Verbinden Sie Ihren PC oder Ihr Telefon mit diesem Zugangspunkt.
Sie können rdzTTGOsonde auch so konfigurieren, dass eine Verbindung zu einem vorhandenen WLAN-Netz hergestellt wird (siehe [[Wifi configuration]]).

Im Zugangspunktmodus können Sie dann über [http://192.168.4.1] (http://192.168.4.1) auf die Software zugreifen. Wenn Sie rdzTTGOsonde so konfigurieren, dass eine Verbindung zu einem vorhandenen WiFi-Netzwerk hergestellt wird, erhält es eine IP-Adresse von diesem Netzwerk über DHCP. In allen Fällen können Sie auch über die URL [http: //rdzsonde.local] (http: //rdzsonde.local) auf das Board zugreifen (sofern Ihr Browser mDNS unterstützt).
