Mit den folgenden Schritten kann man die Arduino IDE so einrichten, dass man den Code selbst kompilieren, ändern und hochladen kann.

# Vorbereitung

## Arduini IDE

Lade die neueste Arduino IDE-Software von arduino.cc/en/Main/Software herunter

## ESP32-Unterstützung

File -> Preferences (oder Arduino -> Preferences unter MacOS)

Unter "Additional Board Manager URLs"

*https://dl.espressif.com/dl/package_esp32_index.json* hinzufügen und OK drücken

Tool -> Board -> Boards Manager

Suche nach "esp32"

Installiere "esp32 by Espressif Systems"

## Unterstützung für das Hochladen des ESP32-Flash-Dateisystemes

Hole die Zip-Datei der neuesten Version von
https://github.com/me-no-dev/arduino-esp32fs-plugin/releases/

Entpacke den Inhalt in den Tools-Ordner der Arduino IDE (~/Documents/Arduino/tools unter MacOS,
ähnlich auf anderen Betriebssystemen), danach die IDE neu starten

# Installation aller erforderlichen Komponenten

## Zusätzliche Bibliotheken

Wähle Tools -> Library Manager

Installiere "U8g2"

Installiere "MicroNMEA"

(Installiere "TFT_22_ILI9225" - derzeit nicht erforderlich)

## Zusätzliche Bibliotheken, Teil 2

Wähle unter https://github.com/me-no-dev/ESPAsyncWebServer "Download ZIP", extrahiere es in den Bibliotheksordner der 
Arduino-IDE (~/Documents/Arduino/libraries unter MacOS), und benenne den Ordner in ESPAsyncWebServer um ("-master" entfernen).

Wähle unter https://github.com/me-no-dev/AsyncTCP "Download ZIP", extrahiere es in den Bibliotheksordner
der Arduino-IDE, und benenne den Hauptordner in AsyncTCP um ("-master" entfernen).

Extrahiere https://github.com/lewisxhe/AXP202X_Library/archive/refs/tags/V1.1.3.zip in den Bibliotheksordner
der Arduino-IDE.

## Zusätzliche Bibliotheken, Teil 3

Kopiere die Verzeichnisse libraries/SX1278FSK und libraries/SondeLib dieses Projekts zum Bibliotheksordner der Arduino-IDE, oder - noch besser - lege symbolische Links an (MacOS / Linux):

```
cd ~/Documents/Arduino/Bibliotheken
ln -s <whereyouclonedthegit>/rdz_ttgo_sonde/libraries/SondeLib/ .
ln -s <whereyouclonedthegit>/rdz_ttgo_sonde/libraries/SX1278FSK/ .
```

Starte die Arduino IDE neu

(symbolische Verknüpfungen sind der bevorzugte Weg, ansonsten muss man die Bibliotheken danach bei jedem Update
erneut kopieren!)

# Letzte Schritte

In der IDE: Tools -> Board: -> Wähle "TTGO LoRa32-OLED v1" (oder T-Beam oder etwas, das dem verwendeten Board entspricht)

Code kompilieren und hochladen

Hochladen von Daten zu SPIFFS mit Tools -> ESP32 Sketch Data Upload