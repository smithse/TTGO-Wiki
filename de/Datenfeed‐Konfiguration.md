# Konfiguration des Datenfeeds

rdzTTGOsonde kann Daten an externe Geräte senden. Derzeit werden AXUDP-Pakete unterstützt, die an aprsmap auf einem PC gesendet werden, und KISS over TCP / IP für APRSdroid.

_ (Hinweis: Daten sind derzeit unvollständig und ungefiltert. Bei DFM-Sonden (die Breiten- und Längengrade in verschiedenen Frames übertragen) werden möglicherweise vorübergehend unvollständige (und damit falsche) Daten gesendet, und der Zeitstempel wird nur aktualisiert, wenn ein DFM-Frame einen enthält (Nicht alle Frames tun dies.) Bitte geben Sie solche Daten nicht an öffentliche Server wie aprs.fi oder radiosondy.info weiter. Es ist in Ordnung für Ihre eigene Karte auf dem Telefon oder PC.) _

## KISS TCP Parameter (APRSdroid)
* Setzen Sie "KISS TNC" auf 1, um den KISS-Dienst auf TCP-Port 14590 zu aktivieren

In APRSdroid müssen Sie konfigurieren
* Anschlüsse: TNC (KISS)
* Art der Verbindung: TCP / IP
* Server für TNC TCP / IP: _IP-Adresse der ESP32-Karte_

APRSdroid stellt eine Verbindung zum rdzTTGOsonde-Board her und empfängt alle Positionsberichte über TCP / IP (AX25 KISS-Frames).

## AXUDP-Parameter (aprsmap)
* Stellen Sie "AXUDP Host" auf die IP-Adresse des Computers ein, auf dem aprsmap ausgeführt wird
* Stellen Sie "AXUDP-Port" auf eine UDP-Portnummer ein, z. B. 9002
* (Tariflimit: derzeit nicht genutzt)

rdzTTGOsonde sendet alle Positionsaktualisierungen unter Verwendung des AXUDP-Protokolls an den konfigurierten Host- und Zielport.

Auf aprsmap müssen Sie konfigurieren
Konfiguration -> HF-Ports -> HF-Port 1 -> ": 9001: 9002"

_ (oder RF-Port 2/3/4; die Portnummer am Ende muss mit dem in der Konfiguration von rdzTTGOsonde konfigurierten Wert übereinstimmen.) _

## APRS-Parameter
(derzeit deaktiviert und nicht verwendet)
* Anruf
* Passcode
* APRS-TCP-Host
* APRS-TCP-Port
* Bewertungslimit

## SondeHub-Parameter

* sondehub.active (Defaultwert 0, auf 1 setzen, um SondeHub-Upload zu aktivieren)
* sondehub.host (Defaultwert api.v2.sondehub.org, nicht ändern)
* sondehub.callsign (Defaultwert CHANGEME_RDZTTGO, hier Stationsnamen/Rufzeichen eintragen)
* sondehub.lat (Defaultwert null, lat/lon auf GPS-Koordinaten für Stationsanzeige auf öffentlicher SondeHub-Karte setzen)
* sondehub.lon (Defaultwert null, lat/lon auf GPS-Koordinaten für Stationsanzeige auf öffentlicher SondeHub-Karte setzen)
* sondehub.alt (Defaultwert null, alt auf Stationshöhe für Stationsanzeige auf öffentlicher SondeHub-Karte setzen)
* sondehub.antenna (verwendete Empfängerantennen, wird auf SondeHub-Karte angezeigt)
* sondehub.email (Email wird an SondeHub gesendet, nur für die Entwickler für Debugging)
