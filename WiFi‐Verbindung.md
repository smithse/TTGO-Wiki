Einige Hinweise zum Zugriff auf das TTGO WiFi, insbesondere unter Android:

Grundlagen: WiFi kann im Station Mode (mit einem Access Point verbunden) oder im Access Point mode (ermöglicht anderen Geräten, sich mit dem TTGO zu verbinden) betrieben werden, siehe [[Software‐Konfiguration]].

Wenn man den Access Point Mode in Kombination mit Android-Handys verwendet, kann man auf folgende Probleme stoßen:

- Wenn man auf einem Android-Handy mobile Daten aktiviert hat und sich mit dem TTGO (im Access Point mode) verbindet, versucht das Telefon "intelligent" zu sein. Es erkennt, dass über den Access Point keine Internetverbindung besteht, und leitet sehr wahrscheinlich den Datenverkehr über mobile Daten anstelle von WiFi weiter. In diesem Fall kann man NICHT auf das TTGO zugreifen (unter Verwendung der IP, die auf dem TTGO angezeigt wird, oder der MDSN-Suche oder der rdzwx-go-App)
- Erste Lösung für dieses Problem: Deaktivierung von mobilen Daten auf dem Handy. Dann wird der gesamte Netzwerkverkehr über die WiFi-Schnittstelle geleitet. Dann kann man auf das TTGO am Handy zugreifen (unter Verwendung der Standard-IP: http://192.168.4.1/ oder der Android-App rdzwx-go).
- Eine bessere Lösung besteht darin, das Handy als Hotspot zu verwenden und das TTGO mit diesem Zugangspunkt zu verbinden. Verwende die vorherigen Schritte, um auf die TTGO-Konfiguration zuzugreifen, lege einen Hotspot-Namen/-Passwort fest, konfiguriere dann das Handy, um den Hotspot zu aktivieren, und starte das TTGO neu (es wird sich mit dem Hotspot verbinden). 
- Das TTGO hat jetzt eine andere IP-Adresse (auf dem Display angezeigt). Verwende `http://<neue IP>/`.
- http://rdzsonde.local/ wird immer funktionieren, anstatt eine IP-Adresse zu verwenden (wenn Ihr System/Browser MDNS-Suche unterstützt).

Zusätzliche Hinweise:
- Für die Verwendung der App rdzwx-go muss "Kiss TNC" in der Konfiguration aktiviert sein (es ist in der Standardkonfiguration aktiviert, nicht deaktivieren!).
- MDNS (d.h. der Zugriff auf das TTGO über `http://rdzsonde.local`) sollte in den meisten Browsern auf PCs (jedes Betriebssystem), auf iOS und auf Android ab Version 12 funktionieren. Es wird NICHT direkt von Android 11 und früher unterstützt, d.h. dies wird im Browser NICHT funktionieren. Die Android-App rdzwx-go enthält Code, um MDNS-Suchen in älteren Android-Versionen durchzuführen und findet automatisch die IP-Adresse des TTGO (im lokalen Netzwerk).

