# VRAM GPU Desk 1.24

## Neu in 1.24 — 60 Tage Aktivierungszeitraum und Offline-Geräteaktivierung

**Pfad des geschützten Zustands und Steuerungsstart korrigiert.** Der Aktivierungszustand verwendet jetzt den kanonischen Windows-Ordner für rechnerweite Daten, auch bei geplanten Aufgaben mit minimaler Umgebung. Damit wird ein Fehler bei relativen Pfaden und Berechtigungen behoben, der den Start der nativen GPU-Steuerung blockieren konnte. Eigentümer-, Zugriffs- und Wiederherstellungsprüfungen bleiben aktiv; andere GPU-Werkzeuge werden nicht exklusiv ausgesperrt.

**60 Tage ab dem ersten unterstützten Start auf diesem Computer.** Der Zeitraum beginnt, wenn eine Ausgabe mit Aktivierung erstmals auf dem Gerät läuft, nicht anhand älterer, ungeprüfter Nutzungsdaten. Der geschützte lokale Startzeitpunkt bleibt bei gewöhnlichen Updates sowie Deinstallation und Neuinstallation erhalten. Ein Update allein startet keine neuen 60 Tage und beendet nach Ablauf keine Hinweise.

**Hinweise ohne Funktionseinschränkungen.** Nach Ablauf bleiben sämtliche Funktionen verfügbar. Während die Anwendung läuft, erscheint mindestens einmal pro Stunde ein lokalisierter, nichtmodaler Hinweis über gewöhnlichen Windows-Fenstern. Danach wird das Kontrollkästchen Aktivierung sichtbar. Das Öffnen oder Schließen des Aktivierungsdialogs deaktiviert weder GPU-Steuerung noch Kühlung, Überwachung oder Prozessaktionen.

**Offline-Anfrage und Antwort mit jeweils 20 Zeichen.** Öffnen Sie die Aktivierung, erstellen Sie eine Geräteanfrage und speichern Sie den 20-stelligen Code als UTF-8-TXT-Datei. Der Eigentümer erstellt mit einem privaten Generator einen passenden, an die Geräteidentität gebundenen Antwortschlüssel mit 20 Zeichen. Geben Sie ihn in der Anwendung ein; eine gültige Antwort beendet die Hinweise. Ändert sich die Computeridentität, kann eine neue Antwort erforderlich sein; der ursprüngliche Zeitraum beginnt dabei nicht erneut.

**Lokaler Zustand und privater Aussteller.** Die Anfrage ist ein undurchsichtiger, vom Gerät abgeleiteter Code; der Aktivierungsvorgang lädt keine HWID ins Internet hoch. Generator und Master-Schlüsseldatei des Eigentümers werden nicht veröffentlicht. Die kompakte Offline-Prüfung garantiert keinen Schutz vor Reverse Engineering oder Manipulation der Anwendung. Gespeicherte Einstellungen, Temperatur-/Kühlungsregelung und der Hell-Dunkel-Kontrast von System/Graphite bleiben erhalten.

[Windows x64 EXE](downloads/VRAM-GPU-Desk-1.24-Setup-x64.exe) · [ZIP](downloads/VRAM-GPU-Desk-1.24-Installer.zip)

# VRAM GPU Desk 1.23

## Neu in 1.23 — kompakte Zahlenfelder und einheitlicher Designkontrast

**Sieben Zahlenfelder mit horizontalen −/+-Tasten.** Temperaturziel, Überhitzungswarnschwelle, Leerlauf-Kühlziel, Mindestlüfterprozent, GPU-Lastschwelle für den Notfall, Aktualisierungsintervall und Overlay-Skalierung verwenden kompakte Felder mit integrierten Einheiten und einem schmalen Farbakzent. Tastatureingabe und dynamische Modellgrenzen einschließlich gemeldeter Hardwaregrenzen bleiben erhalten.

**Passende Eingaben in beiden Designs.** Sprach-, Design- und GPU-Auswahl, Suchfeld und Schnellaktionseditor folgen demselben Akzentstil. System verwendet weiße Eingabeflächen mit dunkler Schrift, Graphite dunkle Eingabeflächen mit heller Schrift. Fokus, Auswahl, deaktivierte Zustände und aufklappende Listen folgen dem aktiven Design.

**Höhere eingestellte Grenzen hervorheben.** Das sanfte Temperaturziel erscheint bei **mehr als 80 °C, also ab 81 °C**, in roter Schrift; die Überhitzungswarnschwelle **ab 86 °C**. Die Farbe kennzeichnet den **eingestellten Grenzwert**, nicht die aktuelle GPU-Temperatur oder einen laufenden Temperaturalarm. Regelalgorithmen, Standardwerte von 78/85 °C für Ziel/Warnung und gespeicherte Einstellungen bleiben unverändert. Fortlaufende Wiederherstellung, Anwendungsprotokoll und die Anzeigen für maximalen Kontaktstrom bzw. Anschlussgesamtstrom aus 1.22 bleiben erhalten.

[System — helle Felder](images/temperature-fields-light.png) · [Graphite — dunkle Felder](images/temperature-fields-dark.png)

Windows x64 EXE — `VRAM-GPU-Desk-1.23-Setup-x64.exe` · Installer ZIP — `VRAM-GPU-Desk-1.23-Installer.zip`

# VRAM GPU Desk 1.22

## Neu in 1.22 — dauerhafte Wiederherstellung, Anwendungsprotokoll und eindeutige Netzteilströme

**Fortlaufende Wiederherstellung.** Solange die erzwungene Wiederherstellung aktiviert ist, werden geprüfte Versuche ohne Begrenzung ihrer Anzahl fortgesetzt: nach 5, 10, 30 und danach alle 60 Sekunden. Die zuletzt gewählte EIN/AUS-Einstellung bleibt beim Stoppen und Neustarten des Controllers erhalten. Die nichtmodale Verlustwarnung schließt automatisch erst, wenn frische Telemetrie die Wiederherstellung bestätigt. Prüfungen zu Eigentümerschaft, abgeschlossenem Abbau und Hardwaregrenzen bleiben bestehen; dies gewährt keine exklusive Kontrolle gegenüber MSI Afterburner oder anderen Reglern.

**Anwendungsprotokoll.** Eine eigene Schaltfläche öffnet das Protokoll für Steuerungsverlust, Wiederherstellung und Wiederholungsversuche je GPU sowie Anfangszustände und Änderungen aller steuerungsbezogenen Kontrollkästchen. Jeder Eintrag enthält UTC und Ortszeit. Die Temperaturaufzeichnung beginnt bei **78 °C**, erfasst weitere Änderungen in ganzen Grad und die Rückkehr unter 78 °C. Das Fenster zeigt bis zu 500 Ereignisse der aktuellen Sitzung. UTF-8-Dateien bleiben lokal unter `%LOCALAPPDATA%/VRAMDeskJava/logs/application.log`; Rotation bei 2 MiB mit fünf Archiven.

**Maximaler Kontaktstrom oder Anschlussgesamtstrom.** Für jeden von bis zu zwei physischen GPU-Stromanschlüssen am Netzteil zeigt die Karte den höchsten verfügbaren Einzelkontaktstrom, sobald mindestens ein Wert bekannt ist, auch bei unvollständigen Kontaktdaten. Fehlen Einzelwerte, erscheint stattdessen der gemessene Gesamtstrom des Anschlusses. Die Beschriftungen unterscheiden ausdrücklich **Maximum** und **Gesamtstrom**. Unbekannte Sensoren bleiben —; eine gemessene Null bleibt Null. Tooltips behalten Einzelkontakte und den Gesamtstrom, soweit verfügbar. Ein Schienenstrom wird nicht als Anschlussmessung ausgegeben.

**Aktualisierung einer alten Installation 1.9.** Eine alte Kopie unter LocalAppData kann weiterlaufen, obwohl 1.22 korrekt in Program Files installiert ist; dadurch erscheint die alte Oberfläche ohne neuere Einstellungen. Beenden Sie die alte Kopie vor der Installation über ihr Tray-Menü. Verwenden Sie danach die aktuelle Startmenü-Verknüpfung und prüfen Sie **v1.22**. Verweist eine Verknüpfung noch auf den alten Ordner, öffnen Sie die installierte Kopie in Program Files und korrigieren Sie die Verknüpfung. Ein altes laufendes Fenster bedeutet nicht, dass neue Einstellungen entfernt wurden.

Windows x64 EXE — `VRAM-GPU-Desk-1.22-Setup-x64.exe` · Installer ZIP — `VRAM-GPU-Desk-1.22-Installer.zip`

# VRAM GPU Desk 1.21

## Neu in 1.21 — optionale Netzteilüberwachung und automatischer Overlay-Kontrast

**Optionales Layout.** Ist die Netzteilüberwachung AUS oder wird kein kompatibles Netzteil erkannt, bleibt die Netzteilkarte ausgeblendet; die anderen Karten nutzen die verfügbare Breite ohne leeren Platzhalter. Nach Erkennung eines Netzteils bleibt dessen Karte bei vorübergehend fehlenden Messwerten mit Strichen sichtbar.

**Kompakteres Dashboard.** Die Karte „Zeit mit VRAM > 50 %“ wurde aus den Ansichten für eine und zwei GPUs entfernt. Die 30-Tage-Anwendungsrangliste und gespeicherte Historie bleiben erhalten.

**Die Netzteilüberwachung ist standardmäßig AUS.** Ein separates Kontrollkästchen ergänzt eine Netzteilkarte mit verfügbarer Ausgangsleistung und den Strömen von bis zu zwei tatsächlichen GPU-Stromanschlüssen. Fehlende oder veraltete Werte erscheinen als —; Schienenströme gelten nicht als einzelne Anschlussströme. Das separate geschützte Lesemodul wird bei der einmaligen UAC-Einrichtung installiert und übernimmt keine GPU-Steuerung.

**Die Kompatibilität hängt vom Modell ab.** Das reine Auslesen wurde mit MSI MPG Ai1300TS geprüft. Ai1600TS ist anhand des Protokolls qualifiziert. Ausgewählte Corsair HXi/RMi, Thermaltake DPS G/iRGB PLUS und zusätzlich NZXT E bestanden synthetische Protokollprüfungen; Hardwareprüfungen stehen aus. Corsair liefert gemessene Ausgangsleistung, Thermaltakes Summe aus Schienenwerten ist ausdrücklich berechnet; NZXT liefert Schienendaten ohne erfundene Gesamtleistung. be quiet! Dark Power Pro 14 IO wurde untersucht; für Seasonic OptiGuard und ASUS ist kein Leser qualifiziert. Keine pauschale Unterstützung aller sechs Marken. Siehe [Netzteilkompatibilität](docs/psu-compatibility.md).

**Automatischer Overlay-Textkontrast ist standardmäßig EIN.** Der Text passt sich dem Hintergrund an; zum manuellen Wählen heller/dunkler Schrift die Option deaktivieren. Transparenz, kompakte Anzeigen, zwei getrennte NVIDIA-Overlays, Doppelklick zum Hauptfenster, Positionen und Temperaturfarben/Töne bleiben erhalten.

Die Graphit-Abbildungen verwenden synthetische Demonstrationswerte, einschließlich Netzteildaten. GPU-Einstellungen, Prozessaktionen, Notfallmodi und gespeicherte Entscheidungen bleiben erhalten.

Windows x64 EXE — `VRAM-GPU-Desk-1.21-Setup-x64.exe` · Installer ZIP — `VRAM-GPU-Desk-1.21-Installer.zip`
