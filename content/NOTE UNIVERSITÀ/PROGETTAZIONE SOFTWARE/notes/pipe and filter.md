si distingue come il modello di riferimento per i sistemi di elaborazione dati. La pipe rappresenta un flusso di dati, mentre il processo rappresenta un filtro

l concetto centrale di questo pattern è la trasformazione funzionale dei dati.

- **Trasformazioni (Filtri):** I componenti del sistema sono visti come trasformazioni che elaborano i loro input per produrre output.
- **Flusso (Pipe):** I dati fluiscono da un filtro all'altro attraverso le "pipe".
- **Modello:** Quando le trasformazioni sono sequenziali, questo pattern segue un modello "batch sequential".

![[Pasted image 20260117161034.png]]

In pratica è una succesione di filtri successivi

Il nome deriva esplicitamente dalla shell di **UNIX**, dove comandi discreti possono essere concatenati.

![[Pasted image 20260117161415.png]]
Il pipe ha una dimensione finita.

Questo pattern viene utilizzato nei seguenti contesti

-  **Ideale per:** 
	Applicazioni di elaborazione dati ("data processing"), sia basate su transazioni che batch, dove gli input vengono elaborati in stadi separati per generare output correlati. Esempi citati includono i sistemi di elaborazione delle fatture e i compilatori.
- **Non adatto per:** 
	Sistemi interattivi. La natura sequenziale e trasformativa del flusso non si sposa bene con la necessità di gestire eventi utente asincroni e immediati.

Vantaggi

- **Semplicità:** È facile da comprendere e supporta il riuso delle trasformazioni (un filtro creato per un sistema può essere usato in un altro). Chiarisce per bene gli assegnamenti di responsabilità
- **Workflow:** Lo stile del flusso di lavoro corrisponde alla struttura di molti processi di business reali.
- **Evoluzione:** È semplice far evolvere il sistema aggiungendo nuove trasformazioni alla catena.
- **Concorrenza:** Può essere implementato sia come sistema sequenziale che concorrente.

Svantaggi

- **Overhead di Parsing:** Questo è il difetto principale. Ogni singola trasformazione (filtro) deve analizzare (parse) il suo input e formattare (unparse) il suo output. Questo aumenta il carico di lavoro del sistema ("System overhead"). Le interfacce dei filtri devono essere decisi antecedente.
- **Formato dei Dati:** I filtri devono concordare sul formato del trasferimento dati. In pratica devono fare il parsing dei dati in input e unparsing in output. Se due filtri usano strutture dati incompatibili, il riuso diventa difficile o impossibile.