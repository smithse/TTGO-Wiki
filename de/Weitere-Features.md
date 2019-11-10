## Over-the-Air-Updates

Wenn Ihr Board mit einem WLAN-Zugangspunkt verbunden ist (d. H. WLAN-Client-Modus, nicht Zugriffspunkt-Modus), können Sie ein drahtloses Update auf die neueste Version des Master- oder Entwicklungszweigs durchführen. Einfach zugreifen

[http: //rdzsonde.local/update.html] (http: //rdzsonde.local/update.html)

Dadurch wird nur die Software aktualisiert, nicht das Dateisystem. In einigen Versionsaktualisierungen ändert sich der Inhalt des Dateisystems, und einige Dinge funktionieren möglicherweise nicht wie erwartet. In diesen Fällen müssen Sie ein Vollversions-Upgrade über USB durchführen.


## Datei-Editor

http: //rdzsonde.local/edit.html? filename

Sie können jede kleine Textdatei im Flash-Dateisystem bearbeiten. ** Beachten Sie, dass Sie durch unerwartete Änderungen das System vollständig beschädigen können, sodass das System erneut in einen stabilen Zustand versetzt werden muss. **
* config.txt _speichert alle Optionen auf der Registerkarte Config, besser über das Webinterface bearbeiten_
* qrg.txt _speichert alle Einträge im QRG-Tab, besser über das Webinterface bearbeiten_
* networks.txt _speichert alle Einträge im WiFi-Tab, besser über das Webinterface bearbeiten_
* index.html _die Hauptseite des Webinterfaces_
* style.css _die Style-Datei der Hauptseite des Webinterface_
* screens.txt _die Display-Layout-Konfiguration, siehe unten für Details_

Wenn Sie während eines vollständigen System-Upgrades einen Teil der Konfiguration beibehalten möchten, können Sie über die oben angegebene URL auf die Datei zugreifen, den Dateiinhalt kopieren, Ihr Board erneut flashen und die neu geflashte Konfiguration durch den kopierten Inhalt ersetzen. 
