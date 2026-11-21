# VRAM GPU Desk 1.22

## Neu in 1.22 — dauerhafte Wiederherstellung, Anwendungsprotokoll und eindeutige Netzteilströme

**Fortlaufende Wiederherstellung.** Solange die erzwungene Wiederherstellung aktiviert ist, werden geprüfte Versuche ohne Begrenzung ihrer Anzahl fortgesetzt: nach 5, 10, 30 und danach alle 60 Sekunden. Die zuletzt gewählte EIN/AUS-Einstellung bleibt beim Stoppen und Neustarten des Controllers erhalten. Die nichtmodale Verlustwarnung schließt automatisch erst, wenn frische Telemetrie die Wiederherstellung bestätigt. Prüfungen zu Eigentümerschaft, abgeschlossenem Abbau und Hardwaregrenzen bleiben bestehen; dies gewährt keine exklusive Kontrolle gegenüber MSI Afterburner oder anderen Reglern.

**Anwendungsprotokoll.** Eine eigene Schaltfläche öffnet das Protokoll für Steuerungsverlust, Wiederherstellung und Wiederholungsversuche je GPU sowie Anfangszustände und Änderungen aller steuerungsbezogenen Kontrollkästchen. Jeder Eintrag enthält UTC und Ortszeit. Die Temperaturaufzeichnung beginnt bei **78 °C**, erfasst weitere Änderungen in ganzen Grad und die Rückkehr unter 78 °C. Das Fenster zeigt bis zu 500 Ereignisse der aktuellen Sitzung. UTF-8-Dateien bleiben lokal unter `%LOCALAPPDATA%/VRAMDeskJava/logs/application.log`; Rotation bei 2 MiB mit fünf Archiven.

**Maximaler Kontaktstrom oder Anschlussgesamtstrom.** Für jeden von bis zu zwei physischen GPU-Stromanschlüssen am Netzteil zeigt die Karte den höchsten verfügbaren Einzelkontaktstrom, sobald mindestens ein Wert bekannt ist, auch bei unvollständigen Kontaktdaten. Fehlen Einzelwerte, erscheint stattdessen der gemessene Gesamtstrom des Anschlusses. Die Beschriftungen unterscheiden ausdrücklich **Maximum** und **Gesamtstrom**. Unbekannte Sensoren bleiben —; eine gemessene Null bleibt Null. Tooltips behalten Einzelkontakte und den Gesamtstrom, soweit verfügbar. Ein Schienenstrom wird nicht als Anschlussmessung ausgegeben.

**Aktualisierung einer alten Installation 1.9.** Eine alte Kopie unter LocalAppData kann weiterlaufen, obwohl 1.22 korrekt in Program Files installiert ist; dadurch erscheint die alte Oberfläche ohne neuere Einstellungen. Beenden Sie die alte Kopie vor der Installation über ihr Tray-Menü. Verwenden Sie danach die aktuelle Startmenü-Verknüpfung und prüfen Sie **v1.22**. Verweist eine Verknüpfung noch auf den alten Ordner, öffnen Sie die installierte Kopie in Program Files und korrigieren Sie die Verknüpfung. Ein altes laufendes Fenster bedeutet nicht, dass neue Einstellungen entfernt wurden.

[Windows x64 EXE](downloads/VRAM-GPU-Desk-1.22-Setup-x64.exe) · [Installer ZIP](downloads/VRAM-GPU-Desk-1.22-Installer.zip)

# VRAM GPU Desk 1.21

## Neu in 1.21 — optionale Netzteilüberwachung und automatischer Overlay-Kontrast

**Optionales Layout.** Ist die Netzteilüberwachung AUS oder wird kein kompatibles Netzteil erkannt, bleibt die Netzteilkarte ausgeblendet; die anderen Karten nutzen die verfügbare Breite ohne leeren Platzhalter. Nach Erkennung eines Netzteils bleibt dessen Karte bei vorübergehend fehlenden Messwerten mit Strichen sichtbar.

**Kompakteres Dashboard.** Die Karte „Zeit mit VRAM > 50 %“ wurde aus den Ansichten für eine und zwei GPUs entfernt. Die 30-Tage-Anwendungsrangliste und gespeicherte Historie bleiben erhalten.

**Die Netzteilüberwachung ist standardmäßig AUS.** Ein separates Kontrollkästchen ergänzt eine Netzteilkarte mit verfügbarer Ausgangsleistung und den Strömen von bis zu zwei tatsächlichen GPU-Stromanschlüssen. Fehlende oder veraltete Werte erscheinen als —; Schienenströme gelten nicht als einzelne Anschlussströme. Das separate geschützte Lesemodul wird bei der einmaligen UAC-Einrichtung installiert und übernimmt keine GPU-Steuerung.

**Die Kompatibilität hängt vom Modell ab.** Das reine Auslesen wurde mit MSI MPG Ai1300TS geprüft. Ai1600TS ist anhand des Protokolls qualifiziert. Ausgewählte Corsair HXi/RMi, Thermaltake DPS G/iRGB PLUS und zusätzlich NZXT E bestanden synthetische Protokollprüfungen; Hardwareprüfungen stehen aus. Corsair liefert gemessene Ausgangsleistung, Thermaltakes Summe aus Schienenwerten ist ausdrücklich berechnet; NZXT liefert Schienendaten ohne erfundene Gesamtleistung. be quiet! Dark Power Pro 14 IO wurde untersucht; für Seasonic OptiGuard und ASUS ist kein Leser qualifiziert. Keine pauschale Unterstützung aller sechs Marken. Siehe [Netzteilkompatibilität](docs/psu-compatibility.md).

**Automatischer Overlay-Textkontrast ist standardmäßig EIN.** Der Text passt sich dem Hintergrund an; zum manuellen Wählen heller/dunkler Schrift die Option deaktivieren. Transparenz, kompakte Anzeigen, zwei getrennte NVIDIA-Overlays, Doppelklick zum Hauptfenster, Positionen und Temperaturfarben/Töne bleiben erhalten.

Die Graphit-Abbildungen verwenden synthetische Demonstrationswerte, einschließlich Netzteildaten. GPU-Einstellungen, Prozessaktionen, Notfallmodi und gespeicherte Entscheidungen bleiben erhalten.

[Windows x64 EXE](downloads/VRAM-GPU-Desk-1.21-Setup-x64.exe) · [Installer ZIP](downloads/VRAM-GPU-Desk-1.21-Installer.zip)
