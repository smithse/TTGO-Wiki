# Software-Konfiguration
(Auf der Registerkarte "** Config **" der Weboberfläche)

## Wifi mode (0/1/2/3) (`` wifi``)
- 0: WLAN deaktiviert
- 1: WLAN-Sendermodus. Stellt im Hintergrund eine Verbindung zum AP her und ruft dynamisch eine IP-Adresse ab (Verbindung in Ordnung: IP-Adresse wird im Display angezeigt). Die Verbindung wird zu einem Netzwerk hergestellt, das auf der Registerkarte "WiFi" / "network.txt" mit dem besten RSSI-Wert konfiguriert ist. Stellt die Verbindung bei einem Verbindungsfehler automatisch wieder her.
- 2: Wifi AP-Modus. Erstellt einen Zugangspunkt (AP-Symbol + IP-Adresse 192.168.4.1. Wird im Display angezeigt). Clients (PC oder Telefon) erhalten eine IP über DHCP
- 3: WLAN-Debug-Modus. Zeigt beim Start das Ergebnis des Netzwerkscans auf dem Display und viele Debug-Informationen auf der seriellen Konsole an. versucht, eine Verbindung zum ersten verfügbaren Netzwerk in network.txt herzustellen. Verbindung wird nicht wiederhergestellt, falls eine hergestellte Verbindung später fehlschlägt. Wenn zum Startzeitpunkt kein Netzwerk in der Datei network.txt verfügbar ist, wird die Karte im AP-Modus gestartet.

## Debug mode (0/1) (`` debug``)
1: Zeigt beim Start einige zusätzliche Informationen auf dem Bildschirm an
(Derzeit werden auf jeden Fall viele Debug-Informationen über die serielle Konsole gesendet.)

## Maxsonde (`` maxsonde``)
Anzahl der Einträge in der Registerkarte "QRG". Muss kleiner als 100 sein. Muss auch größer als 0 sein :-)

# Parameter der Spektrumanzeige

## ShowSpectrum (s) (`` spectrum``)
Wenn ein Spektrum> = 0 eingestellt ist, wird der Spektrum-Modus nach dem Neustart gestartet (ansonsten der Scan-Modus).
Bei Spektrum> 0 ist die Spektrumanzeige nur für `` Spektrum`` Sekunden aktiv und wechselt dann automatisch in den Scan-Modus
Stellen Sie -1 ein, um die Spektrumanzeige zu deaktivieren

## Startfreq (MHz) (`` startfreq``)
Startfrequenz in MHz, normalerweise 400 MHz

## Bandbreite (kHz) (`` channelbw``)
Konfigurationswert für RXBW während der Spektrumaufzeichnung (erfordert zusätzliche Tests, wahrscheinlich sollten wir (auch) AGCBW einstellen?)

## Spectrum MHz Marker (`` Marker``)
Anzeige der MHz-Werte (Anfang, Ende) im Spektrum-Modus

## Spectrum Noisefloor (`` Noisefloor``)
RSSI-Wert am unteren Rand der Anzeige
