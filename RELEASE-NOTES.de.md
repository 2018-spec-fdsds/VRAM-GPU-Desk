# VRAM GPU Desk 1.21

## Neu in 1.21 — optionale Netzteilüberwachung und automatischer Overlay-Kontrast

**Optionales Layout.** Ist die Netzteilüberwachung AUS oder wird kein kompatibles Netzteil erkannt, bleibt die Netzteilkarte ausgeblendet; die anderen Karten nutzen die verfügbare Breite ohne leeren Platzhalter. Nach Erkennung eines Netzteils bleibt dessen Karte bei vorübergehend fehlenden Messwerten mit Strichen sichtbar.

**Kompakteres Dashboard.** Die Karte „Zeit mit VRAM > 50 %“ wurde aus den Ansichten für eine und zwei GPUs entfernt. Die 30-Tage-Anwendungsrangliste und gespeicherte Historie bleiben erhalten.

**Die Netzteilüberwachung ist standardmäßig AUS.** Ein separates Kontrollkästchen ergänzt eine Netzteilkarte mit verfügbarer Ausgangsleistung und den Strömen von bis zu zwei tatsächlichen GPU-Stromanschlüssen. Fehlende oder veraltete Werte erscheinen als —; Schienenströme gelten nicht als einzelne Anschlussströme. Das separate geschützte Lesemodul wird bei der einmaligen UAC-Einrichtung installiert und übernimmt keine GPU-Steuerung.

**Die Kompatibilität hängt vom Modell ab.** Das reine Auslesen wurde mit MSI MPG Ai1300TS geprüft. Ai1600TS ist anhand des Protokolls qualifiziert. Ausgewählte Corsair HXi/RMi, Thermaltake DPS G/iRGB PLUS und zusätzlich NZXT E bestanden synthetische Protokollprüfungen; Hardwareprüfungen stehen aus. Corsair liefert gemessene Ausgangsleistung, Thermaltakes Summe aus Schienenwerten ist ausdrücklich berechnet; NZXT liefert Schienendaten ohne erfundene Gesamtleistung. be quiet! Dark Power Pro 14 IO wurde untersucht; für Seasonic OptiGuard und ASUS ist kein Leser qualifiziert. Keine pauschale Unterstützung aller sechs Marken. Siehe [Netzteilkompatibilität](docs/psu-compatibility.md).

**Automatischer Overlay-Textkontrast ist standardmäßig EIN.** Der Text passt sich dem Hintergrund an; zum manuellen Wählen heller/dunkler Schrift die Option deaktivieren. Transparenz, kompakte Anzeigen, zwei getrennte NVIDIA-Overlays, Doppelklick zum Hauptfenster, Positionen und Temperaturfarben/Töne bleiben erhalten.

Die Graphit-Abbildungen verwenden synthetische Demonstrationswerte, einschließlich Netzteildaten. GPU-Einstellungen, Prozessaktionen, Notfallmodi und gespeicherte Entscheidungen bleiben erhalten.

[Windows x64 EXE](downloads/VRAM-GPU-Desk-1.21-Setup-x64.exe) · [Installer ZIP](downloads/VRAM-GPU-Desk-1.21-Installer.zip)
