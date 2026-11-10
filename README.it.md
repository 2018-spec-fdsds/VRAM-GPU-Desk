# VRAM GPU Desk

[English](README.md) · [Русский](README.ru.md) · [Deutsch](README.de.md) · [Español](README.es.md) · [Français](README.fr.md) · [Italiano](README.it.md) · [中文](README.zh.md) · [한국어](README.ko.md) · [日本語](README.ja.md) · [العربية](README.ar.md) · [हिन्दी](README.hi.md) · [Tiếng Việt](README.vi.md)

**Monitoraggio locale della memoria GPU e controllo della temperatura per Windows x64.**

Versione **1.10** · [Installer Windows](downloads/VRAM-GPU-Desk-1.10-Setup-x64.exe) · [ZIP di installazione](downloads/VRAM-GPU-Desk-1.10-Installer.zip)

> **Controllo GPU:** Il controllo dei parametri di temperatura della GPU richiede una conferma UAC durante l’installazione del componente di controllo. In seguito, controllo della temperatura e raffreddamento si attivano senza ulteriori richieste UAC. Il solo monitoraggio non richiede UAC.

![VRAM GPU Desk — tema di sistema](images/dashboard-system.png)

## Funzioni

- Mostra VRAM fisica occupata/libera, utilizzo GPU e temperatura con grafici storici compatti.
- Elenca applicazioni e servizi locali che usano memoria GPU, con ricerca, ordinamento e filtro facoltativo **oltre 0,5 GiB**.
- Mostra le dieci applicazioni principali e «Altre» come quote normalizzate delle letture di memoria dei processi osservate negli ultimi 30 giorni. Il totale è 100 %: è una ripartizione storica delle letture, non una suddivisione additiva della VRAM fisica.
- Mostra la percentuale del tempo osservato valido nelle ultime 24 ore con occupazione di VRAM fisica oltre il 50 %. Esclude gli intervalli senza monitoraggio.
- Esporta CSV UTF-8 in un percorso locale scelto.
- Si riduce nell’area di notifica, ripristina la finestra esistente agli avvii successivi e supporta avvio facoltativo con Windows.
- Offre tema di sistema e grafite scuro, dodici lingue e aggiornamento ogni 1–5 secondi, predefinito 2 secondi.
- Controllo termico graduale facoltativo tramite limiti supportati di potenza e frequenza del core. La protezione è indipendente dal refresh dell’interfaccia.
- Raffreddamento a riposo, RPM e icone animate. Le nuove impostazioni richiedono controllo termico e raffreddamento a riposo attivi; una disattivazione manuale salvata viene conservata. Il controllo attivo appare solo dopo connessione confermata.
- Avviso dopo almeno dieci secondi strettamente sopra la soglia scelta di 75–92 °C. I picchi brevi non generano avvisi.
- Opzione di emergenza separata, inizialmente disattivata, per l’applicazione scelta esplicitamente. Chiudere/terminare può perdere lavoro non salvato; processi protetti o non verificabili sono esclusi.

![VRAM GPU Desk — tema grafite](images/dashboard-graphite.png)

## Quattro pulsanti rapidi

Assegna **Chiudi applicazione** o **Termina processo** a uno dei quattro pulsanti e modifica l’assegnazione dal menu `⋮` adiacente. Ogni associazione vale solo per l’istanza scelta: PID, ora di creazione e percorso eseguibile. Alla sua fine non viene selezionato automaticamente un altro processo né un PID riutilizzato.

Il pulsante configurato agisce con un clic **senza ulteriore conferma**. Può andare perso lavoro non salvato. Restano i controlli nativi su processi protetti, critici o non verificabili. L’opzione di emergenza separata è inizialmente disattivata e mantiene il comportamento per l’applicazione selezionata.

## Temperature obiettivo e isteresi

Soglie distinte di arresto/riavvio e brevi attese evitano commutazioni frequenti con letture oscillanti.

| Impostazione | Comportamento effettivo | Motivo |
|---|---|---|
| Obiettivo a riposo, predefinito **32 °C**, regolabile 28–40 °C | Dopo tre secondi a 32 °C o meno a riposo, torna ad AUTO del firmware. Riparte a 36 °C, obiettivo +4 °C. Con obiettivo 35 °C: riparte a 39 °C. | L’isteresi di 4 °C evita avvii/arresti ripetuti. AUTO del firmware decide l’arresto completo delle ventole. |
| Riposo/carico | Fino al 10 % di utilizzo GPU è ammesso riposo; dal 15 % vale la curva di carico. Fra 11 e 14 % resta lo stato precedente. Utilizzo sconosciuto mantiene raffreddamento attivo. | Evita commutazioni per piccole variazioni. |
| Obiettivo termico graduale, 70–88 °C | Potenza e frequenza si adattano gradualmente alla tendenza termica. La temperatura può restare inferiore o superare brevemente l’obiettivo. | Inerzia, sensori e driver impediscono un tetto esatto. È un obiettivo di regolazione, non un arresto di emergenza. |
| Avviso di surriscaldamento | Lettura strettamente superiore alla soglia per almeno dieci secondi. | Ignora picchi brevi. |

La temperatura a riposo **non** è il limite sotto carico prolungato. Ambiente, firmware e driver influenzano temperature e ventole. Non usare contemporaneamente regolatori di ventole/frequenze concorrenti sulla stessa scheda.

## Hardware e requisiti

Per NVIDIA GeForce **RTX 5000 Series**. Monitoraggio e controlli dipendono da GPU e driver; quelli non supportati restano indisponibili, senza simulazione.

Windows 10/11 x64, .NET Framework 4.8 e driver NVIDIA compatibile. Java è incluso, senza installazione separata. L’utente Windows connesso deve essere amministratore con normale token desktop filtrato. L’installer chiede UAC una volta e installa il componente in una cartella Program Files fissa e protetta; non supporta credenziali di un altro amministratore. Due attività protette, solo su richiesta, usano launcher fissi e comunicazione locale tipizzata. Il canale installato è progettato per avviare il controllo senza altre richieste UAC; se l’autenticazione fallisce, resta indisponibile senza altra elevazione.

Versioni del driver e hash DLL non sono limitati da una lista autorizzata. NVML di sistema deve superare firma Windows offline con firmatario NVIDIA Corporation verificato, percorsi sicuri e API richieste. Aggiornare il driver non richiede nuovi hash/versioni. La verifica può fallire se mancano dati locali di attendibilità; l’app non scarica certificati o driver.

## Installazione e privacy

1. Scarica l’installer e confronta SHA-256 con [SHA256SUMS.txt](SHA256SUMS.txt).
2. Esci dalla copia precedente dal menu nell’area di notifica. Avvia normalmente dall’account amministratore connesso e approva UAC. La cartella protetta è fissa.
3. Apri il nuovo collegamento, seleziona GPU e verifica lo stato confermato. Configura controlli e pulsanti. Le impostazioni sono locali; le disattivazioni salvate restano tali.

L’app usa interfacce locali Windows/GPU. Non prevede invii di telemetria, inferenza cloud, aggiornamento automatico o download di modelli in esecuzione. CSV, cronologia e impostazioni restano locali. Questo **non** garantisce isolamento di rete del sistema né comportamento di driver esterni, diagnostica Windows o sincronizzazione.

L’installer non è firmato. L’app è distribuita in binari compilati; **il codice sorgente non è pubblicato in questo repository**. Il bytecode Java non è cifrato né garantito resistente alla decompilazione. Restano gli avvisi di licenza del runtime esterno.

Le schermate usano dati sintetici e stato di controllo simulato. Illustrano l’interfaccia, non dimostrano funzionamento o prestazioni hardware.

## Novità della 1.10

- Quattro pulsanti configurabili legati a un’istanza per chiudere/terminare con un clic, riassegnabili, mantenendo i controlli nativi.
- Descrizioni ridotte, mini-grafici aumentati da 35 a 55 pixel; resta l’icona di notifica ad alto contrasto.
- Installazione unica del componente protetto con UAC. Nuove impostazioni termiche/riposo attive; disattivazioni manuali salvate conservate.
- Correzione prudente degli alias: esclude alias confermati di display indiretto senza rendering, senza unire GPU fisiche distinte per nome o memoria.
- Ripara installazioni incomplete sicure e segnala fase, codice e HRESULT precisi in caso di errore.
- Conserva temi, dodici lingue, cronologia locale, CSV UTF-8, identità GPU e politiche di lease, watchdog e ripristino.

Verificati: 48 casi isolati d’interfaccia in dodici lingue e due temi, icone, impostazioni iniziali, associazioni/esecuzione dei pulsanti, controlli reali di token CLR, percorsi Unicode, tutti i 163 file e hash dei broker incorporati, installazione/disinstallazione isolata e registrazione reale elevata di attività temporanee con rilettura XML/DACL, rollback e pulizia. Le attività **non sono state eseguite**; il test non ha invocato modifiche GPU né attività di produzione.

Il test non ha eseguito l’intero installer di produzione né il successivo controllo GPU senza UAC. Non dimostra prestazioni termiche sotto carico prolungato. Le schermate sono sintetiche con controllo simulato.

## Licenza

L’uso non commerciale è gratuito secondo [PolyForm Noncommercial 1.0.0](LICENSE.md), rispettandone condizioni e obblighi di avviso. L’uso commerciale richiede un’autorizzazione separata. Non è una licenza open source; il codice sorgente dell’applicazione non viene pubblicato. Le licenze dei runtime di terze parti rimangono invariate.
