L'architettura Client-Server è composta da tre elementi fondamentali:

• **Server:** Un insieme di server indipendenti ("stand-alone") che forniscono servizi specifici, come la gestione dei dati o la stampa.

• **Client:** Un insieme di client che richiedono e utilizzano questi servizi.

• **Rete:** L'infrastruttura che permette ai client di accedere ai server, solitamente utilizzando un protocollo di tipo **richiesta-risposta** (come il protocollo HTTP)

Un esempio semplice è la libreria film gestita da un sito
![[Pasted image 20260117154308.png]]
i client (browser web) interagiscono con server distinti: un server per il catalogo (che gestisce l'elenco e le vendite) e un video server (che gestisce lo streaming)

Questo pattern è raccomandato in due situazioni principali:

- Quando dei servizi ben definiti devono essere accessibili da **diverse posizioni geografiche**, o tanti client.
- Quando il carico sul sistema è **variabile**, da parte del cambio di numero o di richieste dai client; in questo caso, l'architettura è utile perché i server possono essere replicati per gestire l'aumento del traffico.

**Vantaggi:**

- **Distribuzione:** I server possono essere distribuiti attraverso una rete.
- **Centralizzazione delle funzionalità:** Le funzionalità generali (come un servizio di stampa) possono essere rese disponibili a tutti i client senza dover essere implementate in ogni singolo server. Servizi distinti sono implementati in server distinti

**Svantaggi:**

- **Punto singolo di guasto (Single point of failure):** Ogni servizio rappresenta un punto critico; se un server fallisce o subisce un attacco (es. Denial-of-Service), il servizio si interrompe.
- **Prestazioni imprevedibili:** La velocità del sistema non dipende solo dal software, ma anche dalle condizioni della rete.
- **Problemi di gestione:** Possono sorgere difficoltà amministrative se i server sono di proprietà di organizzazioni diverse