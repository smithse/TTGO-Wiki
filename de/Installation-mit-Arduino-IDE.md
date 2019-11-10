Mit den folgenden Schritten können Sie die Arduino IDE so einrichten, dass Sie den Code selbst kompilieren, ändern und hochladen können.

# Vorbereitung

## Arduini IDE

Laden Sie die neueste Arduino IDE-Software von arduino.cc/en/Main/Software herunter

## ESP32-Unterstützung

Datei -> Einstellungen (oder Arduino -> Einstellungen unter MacOS)

gehe zu "Zusätzliche Board Manager URLs"

Fügen Sie * https: //dl.espressif.com/dl/package_esp32_index.json* hinzu und drücken Sie OK

Werkzeug -> Boad -> Boards Manager

Suche nach "esp32"

Installiere "esp32 by Espressif Systems"

## Unterstützung für das Hochladen von Flash-Dateisystemen mit ESP32

Holen Sie sich die Zip-Datei der neuesten Version von
https://github.com/me-no-dev/arduino-esp32fs-plugin/releases/

Entpacken Sie den Inhalt in den Tools-Ordner Ihrer Arduino IDE (~ / Documents / Arduino / tools unter MacOS,
ähnlich auf anderen Betriebssystemen) und starten Sie die IDE neu

# Installieren Sie alle erforderlichen Komponenten

## Zusätzliche Bibliotheken

Wählen Sie Tools -> Library Manager

Installiere "U8g2"

Installieren Sie "MicroNMEA"

(Installieren Sie "TFT_22_ILI9225" - derzeit nicht erforderlich)

## Zusätzliche Bibliotheken, Teil 2

Wählen Sie unter https://github.com/me-no-dev/ESPAsyncWebServer "ZIP herunterladen" und extrahieren Sie es in die Bibliotheken
Benennen Sie den Hauptordner Ihrer Arduino IDE (~ / Documents / Arduino / libraries unter MacOS) in ESPAsyncWebServer um
(entferne den "-master")

Wählen Sie unter https://github.com/me-no-dev/AsyncTCP "ZIP herunterladen" und extrahieren Sie es in den Bibliotheksordner
von Ihrer Arduino IDE und benennen Sie den Hauptordner in AsyncTCP um

## Zusätzliche Bibliotheken, Teil 3

Kopieren Sie die Bibliotheken / SX1278FSK und die Bibliotheken / SondeLib dieses Projekts in die Bibliotheken Ihrer Arduino IDE
Ordner oder alternativ symbolische Links erstellen (MacOS / Linux):

`` `
cd ~ / Documents / Arduino / Bibliotheken
ln -s <whereyouclonedthegit> / rdz_ttgo_sonde / libraries / SondeLib /.
ln -s <whereyouclonedthegit> / rdz_ttgo_sonde / libraries / SX1278FSK /.
`` `

Starten Sie die Arduino IDE neu

(symbolische Verknüpfungen sind der bevorzugte Weg, ansonsten müssen Sie die Bibliotheken danach erneut kopieren
jedes Update)

# Letzte Schritte

In den IDE Tools -> Board: ->
Wählen Sie "TTGO LoRa32-OLED v1" (oder T-Beam oder etwas, das Ihren Anforderungen entspricht)

Code kompilieren und hochladen

Hochladen von Daten zu SPIFFS mit Extras -> Hochladen von ESP32-Skizzendaten
