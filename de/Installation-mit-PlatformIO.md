# Installation mit PlatformIO

Man kann nun auch PlatformIO als Entwicklungsplattform an Stelle von Arduino IDE verwenden. PlatformIO vereinfacht die Verwaltung von Abhängigkeiten. Es können sowohl die Kommandozeilentools von PlatformIO Core verwendet werden, als auch die PlatformIO IDE als Plugin für verschiedene Entwicklungsumgebungen.

Zur Installation siehe auch https://platformio.org/install für weitere Details.

Untenstehend eine Kurzbeschreibung zur Installation von PlatformIO Core in einem Python virtual environment.  Ebenso kann natürlich auch die graphische IDE von PlatformIO verwendet werden. Dazu sollten sich zahlreiche Tutorials online finden lassen (z. B. über den zuvorstehenden Link)

## Setup

(Linux oder MacOS; kleine Anpassungen unter Windows erforderlich)

(Erstes Kommando nur, falls virtualenv noch nicht installiert sein sollte; Python muss bereits installiert sein.)
```
pip install virtualenv
virtualenv ~/.platformio/penv
```

Falls Fehlermeldungen zu "locale" erscheinen, müssen environment-Variablen für Python 3 gesetzt werden (zur Installation ebenso wie zur Nutzung unten),
z. B. so:
```
export LC_CTYPE=de_DE.UTF-8
export LANG=de_DE.UTF-8 
```

## Verwenden

Python-environment aktivieren und Code kompilieren (alle abhängigen Pakete werden automatisch installiert!):
```
. ~/.platformio/penv/bin/activate
pio run -e ttgo-lora32-v1
```

Code und Dateisystem auf das Board laden (Code wird bei Bedarf ebenfalls automatisch kompiliert):
```
pio run -e ttgo-lora32-v1 --target upload
pio run -e ttgo-lora32-v1 --target uploadfs 
```

Hinweis: Das Environment "ttgo-lora32-v1" eignet sich zum Erstellen eines Binärimages, das mit allen [[unterstützten Boards|Unterstützte Boards]] kompatibel ist.

Serial port monitor mit Debug-Daten:
```
pio device monitor
```
