A Questo dobbiamo arrivare arrivare ad una versione consolidata e finale del documento dei requisiti (completo e corretto). Questo documento può includere alla fine anche:
- Test di accettazione
- Piano di sviluppo
- contratto del progetto software

Prima di ciò avviene un processo che serve per evitare errori in produzione, in quanto è possibile in questa fase di scoprire nuovi errori

Quindi il controllo di qualità consiste nel:
- identificare e controllare errori nei requisiti con
	- validazione
	- verficazione
	- check
- documentazione dei difetti


---
### Come si affronta la revisione

per verificare la qualità dei documenti dei requisiti si può fare una ispezione e revisione

L’idea è quella di avere uno o più esperti che prendono il documento dei requisiti che prendono il documento dei requisiti e lo analizzano oppure utilizzare dei meeting di gruppo per discutere il documento. Può avvenire attraverso
- Walkthrough
	ispezione del documento punto per punto
- in modo strutturato
	discussioni di parti del documento anche con meeting, si segue un processo in maniera iterativa
	![[Pasted image 20250609111039.png]]


---
### Linee guida per la revisione

alcune linee guida sono:

-  Rapporto di Ispezione:
	- Deve essere informativo, accurato e costruttivo.
	- Non deve contenere opinioni personali o commenti che possano risultare offensivi.
	- Deve seguire una struttura standard che permetta l’aggiunta di commenti liberi e sia di facile lettura. 
	- Può servire da guida per la revisione individuale. 
- Gli Ispettori: 
	- Devono essere indipendenti dagli autori del documento sotto revisione.
	- Devono rappresentare tutti gli stakeholder e provenire da background diversi.
-  Tempistica dell’Ispezione: 
	- L’ispezione non deve avvenire n´e troppo presto n´e troppo tardi. 
	- Incontri brevi e ripetuti risultano più efficaci. 
-  Focus Maggiore su Parti Critiche:
	- Maggiore è il numero di difetti in una parte, maggiore deve essere lo scrutinio su quella parte.

La revisione deve essere fatta nel momento opportuno, non troppo presto ma neanche troppo tardi

---
### Checklist

L’obiettivo principale delle liste di controllo per l’ispezione è di dirigere la ricerca dei difetti verso specifiche problematiche, migliorando così l’efficienza e l’efficacia del processo di revisione. Le liste di controllo si suddividono in diverse categorie, ognuna con un focus particolare

- Liste basate sui difetti
	Queste liste comprendono domande generiche che sono strutturate in base al tipo di difetto. L’intento è di coprire un ampio spettro di possibili anomalie in modo organizzato.
	![[Pasted image 20250609120048.png]]
	![[Pasted image 20250609120056.png]]
	![[Pasted image 20250609120104.png]]

- Liste specifiche per qualità
	Tali liste affinano le domande delle liste basate sui difetti per concentrarsi su specifiche categorie di requisiti non funzionali (NFR), come la sicurezza, la performance e l’usabilità. Queste liste possono anche essere basate su parole guida e sono frequentemente orientate a identificare omissioni, migliorando così la completezza del software o del prodotto analizzato.

- Liste specifiche per dominio
	Queste liste rappresentano un’ulteriore specializzazione e si concentrano su concetti e le operazioni specifici di un dominio. Sono particolarmente utili per offrire una guida dettagliata nella ricerca di difetti, assicurando che le peculiarità del dominio siano adeguatamente considerate.

- Liste basate sul linguaggio
	Queste liste adattano le liste basate sui difetti ai costrutti di linguaggi di specifica particolari, supportando processi di automazione. La ricchezza dei linguaggi di specifica consente implementazioni di controlli più sofisticati e mirati.

![[Pasted image 20250609120554.png]]
![[Pasted image 20250609120603.png]]


---
### Query

le query sono un'altra forma di quality assurance, in pratica ci sono tool automatici che dal documento e dai diagrammi estraggono informazioni da inserire in un database. 

La verifica della consistenza dei dati viene effettuata attraverso query
![[Pasted image 20250609121346.png]]
Quando si formulano tali query utilizzando i CASE tools, si possono ottenere delle risposte automatiche

![[Pasted image 20250609121614.png]]


---
### Animazioni

sono simili ai scenari, sono molto funzionali perchè permette di validare i requisiti non solo con gli ingegneri dei requisiti ma anche con gli stakeholders e hanno due approcci:
- da uno state machine estrarre possibili scenari di interazione in azione 
- una volta ottenuti gli scenari usare programmi di animazione per le specifiche
	1. Generazione del Modello Esecutivo: Si estrae o si genera un modello eseguibile direttamente dalle specifiche tecniche. 
	2. Simulazione del Comportamento: Il sistema viene simulato basandosi su questo modello, dove eventi stimolo vengono inviati per imitare il comportamento dell’ambiente circostante e si osserva la risposta del modello. 
	3. Visualizzazione della Simulazione: La simulazione viene visualizzata mentre è in corso, permettendo una valutazione immediata e dinamica del comportamento del sistema.
	4. Feedback degli Utenti: I feedback degli utenti vengono raccolti e analizzati per valutare l’efficacia della simulazione e del modello proposto

![[Pasted image 20250609122629.png]]
![[Pasted image 20250609122636.png]]