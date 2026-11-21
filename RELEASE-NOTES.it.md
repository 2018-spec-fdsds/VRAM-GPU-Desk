# VRAM GPU Desk 1.24

## Novità della versione 1.24 — periodo di 60 giorni e attivazione offline del dispositivo

**Corretti il percorso dello stato protetto e l’avvio del controllo.** Lo stato di attivazione usa la cartella canonica dei dati Windows condivisi dal computer, anche con attività pianificate in un ambiente minimo. Si evita così un errore di percorso relativo e autorizzazioni che poteva bloccare l’avvio del controllo GPU nativo. Restano attive le verifiche di proprietario, accesso e ripristino; non viene garantito il controllo esclusivo rispetto ad altre utilità GPU.

**60 giorni dal primo avvio supportato su questo computer.** Il periodo inizia quando un’edizione con attivazione viene eseguita per la prima volta sul dispositivo, senza utilizzare vecchi registri non verificati. La data iniziale locale protetta viene conservata durante gli aggiornamenti ordinari e la disinstallazione/reinstallazione. Il solo aggiornamento non riavvia i 60 giorni e non interrompe i promemoria dopo la scadenza.

**Promemoria senza limitazioni funzionali.** Al termine del periodo tutte le funzioni restano disponibili. Mentre l’applicazione è in esecuzione compare almeno una volta all’ora un promemoria localizzato e non modale sopra le normali finestre di Windows. A quel punto diventa visibile la casella Attivazione. Aprire o chiudere il dialogo non disattiva controllo GPU, raffreddamento, monitoraggio o azioni sui processi.

**Richiesta e risposta offline di 20 caratteri.** Apri Attivazione, genera una richiesta del dispositivo e salva il codice di 20 caratteri in un TXT UTF-8. Il proprietario usa un generatore privato per creare una risposta di 20 caratteri legata a quell’identità. Inseriscila nell’applicazione: una risposta valida interrompe i promemoria. Se cambia l’identità del computer, potrebbe servire una nuova risposta; il periodo originale non ricomincia.

**Stato locale ed emittente privato.** La richiesta è un codice opaco derivato dal dispositivo; la procedura di attivazione non carica l’HWID su Internet. Il generatore e il file della chiave principale del proprietario non vengono pubblicati. La verifica offline compatta non garantisce protezione da ingegneria inversa o modifiche dell’applicazione. Restano invariati impostazioni salvate, regolazione termica e del raffreddamento e inversione dei campi System/Graphite.

[Windows x64 EXE](downloads/VRAM-GPU-Desk-1.24-Setup-x64.exe) · [ZIP](downloads/VRAM-GPU-Desk-1.24-Installer.zip)

# VRAM GPU Desk 1.23

## Novità della versione 1.23 — campi numerici compatti e contrasto coerente

**Sette campi numerici con pulsanti orizzontali −/+.** Temperatura obiettivo, soglia di avviso di surriscaldamento, obiettivo di raffreddamento in inattività, percentuale minima delle ventole, soglia di carico GPU di emergenza, intervallo di aggiornamento e scala dell’overlay usano campi compatti con unità integrate e un sottile accento di colore. Restano disponibili l’inserimento da tastiera e i limiti dinamici del modello, compresi i limiti hardware comunicati.

**Campi coerenti in entrambi i temi.** I selettori di lingua, tema e GPU, la ricerca e l’editor dei pulsanti rapidi seguono lo stesso stile. System usa campi bianchi con testo scuro; Graphite campi scuri con testo chiaro. Gli stati attivo, selezionato e disabilitato, nonché gli elenchi a discesa, seguono il tema corrente.

**Le soglie configurate più alte risaltano.** La temperatura obiettivo della regolazione graduale appare in rosso **oltre 80 °C, quindi da 81 °C**; la soglia di avviso di surriscaldamento, **da 86 °C**. Il colore descrive la **soglia configurata**, non la temperatura attuale della GPU o un allarme termico in corso. Algoritmi di controllo, valori predefiniti obiettivo/avviso di 78/85 °C e preferenze salvate rimangono invariati. Sono mantenuti il ripristino continuo, il registro e le etichette della corrente massima del contatto o totale del connettore introdotti in 1.22.

[System — campi chiari](images/temperature-fields-light.png) · [Graphite — campi scuri](images/temperature-fields-dark.png)

Windows x64 EXE — `VRAM-GPU-Desk-1.23-Setup-x64.exe` · Installer ZIP — `VRAM-GPU-Desk-1.23-Installer.zip`

# VRAM GPU Desk 1.22

## Novità della versione 1.22 — ripristino continuo, registro e correnti dell’alimentatore più chiare

**Ripristino continuo del controllo.** Finché il ripristino forzato è attivo, i tentativi verificati continuano senza limite di numero: dopo 5, 10, 30 e poi ogni 60 secondi. L’ultima scelta ATTIVO/DISATTIVO viene conservata durante l’arresto e il riavvio del controller. L’avviso non modale di perdita del controllo si chiude automaticamente solo dopo la conferma da telemetria recente. Restano attivi i controlli di proprietà, arresto completo del client precedente e limiti hardware; ciò non fornisce controllo esclusivo rispetto a MSI Afterburner o altri regolatori.

**Registro dell’applicazione.** Un pulsante dedicato apre gli eventi di perdita, ripristino e nuovo tentativo per ogni GPU, oltre agli stati iniziali e alle modifiche di tutte le caselle relative al controllo. Ogni voce contiene ora UTC e locale. La temperatura viene registrata da **78 °C**, con le successive variazioni in gradi interi e il ritorno sotto 78 °C. Il visualizzatore mostra fino a 500 eventi della sessione corrente. I file UTF-8 restano locali in `%LOCALAPPDATA%/VRAMDeskJava/logs/application.log`, con rotazione a 2 MiB e cinque archivi.

**Corrente massima del contatto o totale del connettore.** Per ciascuna delle due porte fisiche di alimentazione GPU al massimo, la scheda mostra la maggiore corrente individuale disponibile se almeno una lettura è nota, anche con dati parziali. In assenza di letture individuali mostra invece la corrente totale misurata del connettore. Le etichette distinguono esplicitamente **massimo** e **totale**. I sensori sconosciuti restano —; uno zero misurato resta zero. Le descrizioni conservano le letture dei contatti e il totale disponibili. La corrente di un rail non sostituisce una misura del connettore.

**Aggiornamento da una vecchia installazione 1.9.** Una copia in LocalAppData può restare in esecuzione anche se 1.22 è correttamente installata in Program Files, mostrando l’interfaccia precedente senza le nuove opzioni. Prima dell’installazione, esci dalla vecchia copia tramite il menu nell’area di notifica; dopo usa il collegamento attuale del menu Start e verifica **v1.22**. Se un collegamento punta ancora alla vecchia cartella, apri la copia installata in Program Files e correggilo. Una vecchia finestra ancora aperta non significa che le nuove impostazioni siano state eliminate.

Windows x64 EXE — `VRAM-GPU-Desk-1.22-Setup-x64.exe` · Installer ZIP — `VRAM-GPU-Desk-1.22-Installer.zip`

# VRAM GPU Desk 1.21

## Novità 1.21 — alimentatore opzionale e contrasto automatico

**Disposizione opzionale.** Se il monitoraggio è disattivato o non viene rilevato un alimentatore compatibile, la sua scheda è nascosta e le altre sfruttano la larghezza disponibile, senza spazi vuoti. Dopo il rilevamento, se le letture sono temporaneamente indisponibili, la scheda rimane visibile con trattini.

**Pannello più compatto.** La scheda «Tempo con VRAM > 50%» è stata rimossa dalle viste con una e due GPU. Restano la classifica delle applicazioni su 30 giorni e la cronologia salvata.

**Il monitoraggio dell’alimentatore è disattivato per impostazione predefinita.** Una casella separata aggiunge una scheda con la potenza di uscita disponibile e le correnti di un massimo di due connettori GPU reali. Valori mancanti o obsoleti mostrano —; le correnti delle linee non vengono presentate come correnti di singoli connettori. Il componente protetto di sola lettura viene installato con l’unica configurazione UAC e non acquisisce il controllo GPU.

**La compatibilità dipende dal modello.** La lettura è stata verificata su MSI MPG Ai1300TS. Ai1600TS è qualificato a livello di protocollo. Alcuni Corsair HXi/RMi, Thermaltake DPS G/iRGB PLUS e, inoltre, NZXT E hanno superato test sintetici; manca la verifica fisica. Corsair fornisce watt misurati, il totale Thermaltake è indicato come calcolato; NZXT fornisce le linee senza inventare un totale. be quiet! Dark Power Pro 14 IO è stato studiato; nessun lettore è qualificato per Seasonic OptiGuard o ASUS. Non si dichiara supporto universale per sei marchi. Vedere [compatibilità degli alimentatori](docs/psu-compatibility.md).

**Il contrasto automatico del testo è attivo per impostazione predefinita.** Il testo si adatta allo sfondo; disattivare l’opzione per scegliere manualmente testo chiaro o scuro. Restano trasparenza, indicatori compatti, due overlay NVIDIA separati, doppio clic verso la finestra, posizioni e colori/suoni della temperatura.

Le immagini in grafite usano dati dimostrativi sintetici, alimentatore incluso. Restano invariati impostazioni GPU, azioni sui processi, modalità di emergenza e preferenze salvate.

Windows x64 EXE — `VRAM-GPU-Desk-1.21-Setup-x64.exe` · Installer ZIP — `VRAM-GPU-Desk-1.21-Installer.zip`
