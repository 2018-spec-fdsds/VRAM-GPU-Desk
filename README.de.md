# VRAM GPU Desk

[English](README.md) · [Русский](README.ru.md) · [Deutsch](README.de.md) · [Español](README.es.md) · [Français](README.fr.md) · [Italiano](README.it.md) · [中文](README.zh.md) · [한국어](README.ko.md) · [日本語](README.ja.md) · [العربية](README.ar.md) · [हिन्दी](README.hi.md) · [Tiếng Việt](README.vi.md)

**Lokale GPU-Speicherüberwachung und Temperaturregelung für Windows x64.**

Version **1.10** · [Windows-Installer](downloads/VRAM-GPU-Desk-1.10-Setup-x64.exe) · [Installations-ZIP](downloads/VRAM-GPU-Desk-1.10-Installer.zip)

![VRAM GPU Desk — Systemdesign](images/dashboard-system.png)

## Funktionen

- Zeigt belegten/freien physischen VRAM, GPU-Auslastung und Temperatur mit kompakten Verlaufsdiagrammen.
- Listet lokale Anwendungen und Dienste mit GPU-Speichernutzung, Suche, Sortierung und optionalem Filter **über 0,5 GiB**.
- Zeigt die zehn größten Anwendungen und „Andere“ als normalisierte Anteile der erfassten Prozessspeicherwerte der letzten 30 Tage. Die Summe beträgt 100 %. Dies ist eine historische Messwertverteilung, keine addierbare Aufteilung des physischen VRAM.
- Zeigt den Anteil der gültig beobachteten Zeit der letzten 24 Stunden mit mehr als 50 % physischer VRAM-Belegung. Überwachungslücken zählen nicht mit.
- Exportiert UTF-8-CSV-Berichte in einen gewählten lokalen Pfad.
- Minimiert in den Infobereich, stellt bei erneutem Start das bestehende Fenster wieder her und unterstützt optionalen Windows-Autostart.
- Bietet System- und dunkles Graphitdesign, zwölf Oberflächensprachen und Aktualisierung alle 1–5 Sekunden, standardmäßig 2 Sekunden.
- Optionale sanfte Temperaturregelung über unterstützte Leistungs-/Kerntaktgrenzen. Der Schutz arbeitet unabhängig vom Aktualisierungsintervall der Oberfläche.
- Leerlaufkühlung, Lüfterdrehzahlen und animierte Symbole. Neue Einstellungen fordern Temperaturregelung und Leerlaufkühlung eingeschaltet an; gespeichertes manuelles AUS bleibt erhalten. Aktive Regelung wird erst nach bestätigter Verbindung angezeigt.
- Warnung nach mindestens zehn Sekunden strikt oberhalb der gewählten Schwelle von 75–92 °C. Kurze Spitzen lösen keine Warnung aus.
- Separate, zunächst ausgeschaltete Notfalloption für die ausdrücklich ausgewählte Anwendung. Schließen/Beenden kann ungespeicherte Arbeit verlieren lassen; geschützte oder nicht überprüfbare Prozesse sind ausgeschlossen.

![VRAM GPU Desk — Graphitdesign](images/dashboard-graphite.png)

## Vier Schnellaktionstasten

Weisen Sie **Anwendung schließen** oder **Prozess beenden** einer der vier kleinen Tasten zu. Das benachbarte Menü `⋮` ändert die Zuweisung. Jede Bindung gilt nur für die ausdrücklich ausgewählte Prozessinstanz: PID, Erstellungszeit und EXE-Pfad. Nach deren Ende werden andere Prozesse oder wiederverwendete PIDs nicht automatisch ausgewählt.

Die konfigurierte Taste arbeitet mit einem Klick **ohne zusätzliche Bestätigung**. Ungespeicherte Arbeit kann verloren gehen. Native Prüfungen geschützter, kritischer und nicht überprüfbarer Prozesse bleiben aktiv. Die separate Notfalloption ist zunächst aus und behält das Verhalten für die ausgewählte Anwendung.

## Temperaturziele und Hysterese

Getrennte Stopp-/Neustartschwellen und kurze Wartezeiten verhindern häufiges Umschalten bei schwankenden Werten.

| Einstellung | Tatsächliches Verhalten | Zweck |
|---|---|---|
| Leerlaufziel, standardmäßig **32 °C**, einstellbar 28–40 °C | Nach drei Sekunden bei höchstens 32 °C im Leerlauf geht die Regelung an Firmware-AUTO zurück. Neustart bei 36 °C, also Ziel +4 °C. Bei Ziel 35 °C: Neustart bei 39 °C. | Die 4-°C-Hysterese verhindert häufige Lüfterstarts. Ob Lüfter ganz stoppen, entscheidet Firmware-AUTO. |
| Leerlauf/Last | Bis 10 % Auslastung ist Leerlauf zulässig; ab 15 % gilt die Lastkurve. Bei 11–14 % bleibt der vorige Zustand. Unbekannte Auslastung hält die Kühlung aktiv. | Verhindert Umschalten durch kleine Schwankungen. |
| Sanftes Temperaturziel, 70–88 °C | Leistungs-/Kerntaktgrenzen werden schrittweise anhand des Temperaturtrends angepasst. Die Temperatur kann unter dem Ziel liegen oder es kurz überschreiten. | Thermische Trägheit, Sensoren und Treiber verhindern eine exakte harte Grenze. Dies ist ein Regelziel, keine Notabschaltung. |
| Überhitzungswarnung | Mindestens zehn Sekunden strikt oberhalb der Schwelle. | Unterdrückt kurze Spitzen. |

Die Leerlauftemperatur ist **nicht** die Grenze unter Dauerlast. Umgebung, Firmware und Treiber beeinflussen erreichbare Temperaturen und Lüfterreaktion. Keine konkurrierenden Lüfter-/Taktregler gleichzeitig für dieselbe Karte verwenden.

## Hardware und Voraussetzungen

Für NVIDIA GeForce **RTX 5000 Series**. Messungen und Regelmöglichkeiten hängen von GPU und Treiber ab; nicht unterstützte Funktionen bleiben nicht verfügbar, statt simuliert zu werden.

Windows 10/11 x64, .NET Framework 4.8 und unterstützter NVIDIA-Treiber. Java ist enthalten; separate Installation ist unnötig. Der angemeldete Benutzer muss Administrator mit normalem gefiltertem Desktop-Token sein. Setup fragt einmal UAC an und installiert in einem festen geschützten Program-Files-Verzeichnis. Anmeldedaten eines anderen Administrators werden nicht unterstützt. Zwei geschützte Aufgaben ohne automatische Trigger verwenden feste Steuerstarter und typisierte lokale Kommunikation. Der installierte Kanal soll Regelung ohne weitere UAC-Abfrage starten; bei fehlgeschlagener Authentifizierung bleibt sie nicht verfügbar, ohne andere Rechteerhöhung.

Treiberversionen und DLL-Hashes werden nicht per Zulassungsliste eingeschränkt. System-NVML muss die Offline-Signaturprüfung von Windows mit bestätigtem NVIDIA-Corporation-Unterzeichner, sicheren Pfaden und erforderlichen APIs bestehen. Treiberupdates brauchen keinen neuen Versions-/Hash-Eintrag. Fehlende lokale Vertrauensdaten können die Offline-Prüfung verhindern; die Anwendung lädt keine Zertifikate oder Treiber.

## Installation und Datenschutz

1. Installer herunterladen und SHA-256 mit [SHA256SUMS.txt](SHA256SUMS.txt) vergleichen.
2. Vorige Kopie über das Infobereichsmenü beenden. Setup normal vom angemeldeten Administratorkonto starten und UAC bestätigen. Der geschützte Installationspfad ist fest.
3. Neue Verknüpfung öffnen, GPU wählen und bestätigten Reglerstatus prüfen. Regler und Schnelltasten konfigurieren. Einstellungen bleiben lokal; gespeichertes AUS bleibt AUS.

Die Anwendung verwendet lokale Windows-/GPU-Schnittstellen. Keine vorgesehenen Telemetrie-Uploads, Cloud-Inferenz, automatische Aktualisierung oder Laufzeit-Modell-Downloads. CSV, Verlauf und Einstellungen bleiben lokal. Dies garantiert **keine** systemweite Netzwerksperre und nichts über Drittanbietertreiber, Windows-Diagnose oder Synchronisierungssoftware.

Der Installer ist nicht signiert. Verteilt werden kompilierte Binärdateien; **der Anwendungsquellcode wird in diesem Repository nicht veröffentlicht**. Java-Bytecode ist nicht verschlüsselt und nicht garantiert gegen Dekompilierung geschützt. Lizenzhinweise der mitgelieferten Laufzeit bleiben erhalten.

Screenshots verwenden synthetische Demonstrationsdaten und simulierten Reglerstatus. Sie zeigen die Oberfläche, keinen Nachweis von Hardwarebetrieb oder Leistung.

## Änderungen in 1.10

- Vier konfigurierbare, instanzgebundene Ein-Klick-Tasten zum Schließen/Beenden, neu zuweisbar bei erhaltenen nativen Schutzprüfungen.
- Kleinere Dashboard-Beschreibungen, Mini-Diagramme von 35 auf 55 Pixel erhöht; kontrastreiches Infobereichssymbol erhalten.
- Geschützte Steuerkomponente einmal mit UAC installieren. Neue Temperatur-/Leerlaufkühleinstellungen an; gespeichertes manuelles AUS bleibt erhalten.
- Konservative Aliaskorrektur: bestätigte indirekte Anzeige-Aliase ohne Renderfunktion ausschließen, ohne getrennte physische GPUs nach Namen oder Speicherwerten zusammenzuführen.
- Sichere unvollständige Installationen reparieren; konkrete Phase, Fehlercode und HRESULT bei Komponentenfehlern anzeigen.
- Beide Designs, zwölf Sprachen, lokaler Verlauf, UTF-8-CSV, GPU-Identitätsprüfungen und bisherige Lease-/Watchdog-/Wiederherstellungsregeln erhalten.

Geprüft: 48 isolierte Oberflächenfälle in zwölf Sprachen und zwei Designs, Infobereichssymbole, Standardwerte, Schnellaktionsbindungen/-ausführung, echte CLR-Tokenprüfungen, Unicode-Pfade, alle 163 Paketdateien und eingebetteten Broker-Hashes, isolierte Installation/Deinstallation sowie echte erhöhte Registrierung temporärer Aufgaben mit XML-/DACL-Rücklesen, Rückabwicklung und Bereinigung. Die Aufgaben wurden **nicht ausgeführt**; keine GPU-Schreibfunktionen oder Produktionsaufgaben wurden durch diesen Test aufgerufen.

Der vollständige produktive Installationsablauf und anschließende GPU-Regelung ohne UAC wurden durch den Registrierungstest nicht ausgeführt. Die Prüfungen belegen keine thermische Leistung unter Dauerlast. Screenshots sind synthetische Demonstrationen mit simuliertem Reglerstatus.
