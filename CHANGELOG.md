
### **File: `CHANGELOG.txt`**


### Versione 2.0.0 (20-06-2025)

Questa versione introduce una riscrittura completa del motore di configurazione e della logica di core di Hyperlisa, rendendolo significativamente più potente e flessibile.

**[BREAKING CHANGE]**
- La struttura del file di configurazione è stata completamente rinnovata. I file `config.yaml` delle versioni precedenti non sono più compatibili.
- Il file di configurazione viene ora gestito all'interno di una directory `.hyperlisa` nella root del progetto.

**[NEW]**
- **Sistema a Profili**: Introdotto un sistema di profili di analisi che permette di definire molteplici configurazioni all'interno di un unico `config.yaml`.
- **Controllo di Profondità (`depth`)**: Ogni percorso può specificare la profondità della scansione (`0` per nessuna ricorsione, `N` per N livelli, `*` per ricorsione infinita).
- **Flag di Attivazione**: Aggiunto il parametro `enable: true|false` per attivare o disattivare selettivamente i profili.
- **Nomenclatura Dinamica**: Introdotto un `name_template` per personalizzare i nomi dei file di output usando i placeholder `$n` (nome progetto), `$ts` (timestamp), e `$p` (nome profilo).
- **Intestazione con Metadati**: Il separatore tra i file ora include un'intestazione robusta con metadati strutturati in formato JSON (`path`, `language`, `lines`, `last_modified`).
- **Supporto Variabili**: Aggiunto il supporto per le variabili (ancore YAML) nel file di configurazione per ridurre la duplicazione.
- **Supporto Wildcard Avanzato**: Pieno supporto al wildcard `**` nei percorsi per la selezione ricorsiva delle directory.
- **Aggiunto il comando `hyperlisa-migrate`** per convertire automaticamente i progetti dal vecchio formato di configurazione al nuovo.
- **Aggiunta la visualizzazione della struttura ad albero** del progetto all'inizio del file di output (disattivabile con `--notree`).
- **Aggiunto il parametro `depth`** nella configurazione per un controllo granulare sulla profondità della scansione delle cartelle.


**[CHANGED]**
- **Comportamento CLI di Default**: Eseguire `cmb` senza argomenti ora processa tutti i profili abilitati, generando un file per ciascuno.
- **Logica di Esclusione**: La logica di matching è ora più stringente: un pattern che termina con `/` si applica solo alle cartelle, altrimenti solo ai file.

**[REMOVED]**
- **Parametro `--all`**: Il parametro `--all` è stato rimosso poiché il suo comportamento è ora quello predefinito del comando `cmb`.
- **Concetto di "Profilo di Default"**: Non esiste più un profilo di default implicito; l'azione di default è processare tutti i profili attivi.

**[FIXED]**
- I file di output vengono ora generati correttamente all'interno della directory `.hyperlisa`, mantenendo pulita la cartella radice del progetto.










