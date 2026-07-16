con questa sezione si conclude il ciclo dei requisiti

![[Pasted image 20250609164101.png]]

In sostanza il processo non si ferma dopo aver consolidato il documento dei requisiti, ma potrebbe iterare il processo fin tanto che non si è soddisfatti.

Si continua con il ciclo perchè potrebbero evolvere dei requisiti e la conoscenza di questi requisiti potrebbero evolversi, di seguito il documento dei requisiti potrà cambiare per sostenere questi nuovi cambiamenti

Dobbiamo creare una metodologia che supporti questa evoluzione


---
### Il cambiamento

I cambiamenti potrebberso essere le **funzionalità** ovvero unità di cambiamento e sono di due tipi:
- Funzionali o non funzionali
- Di ambiente: assunzioni,  vincoli, procedure di lavori,

Siccome è avvenuto un cambiamento, il sistema finale risulterà modificato in due aspetti:
- Revisione
	Per correggere, migliorare singole feature
- Variante
	Diverse versioni del sistema che coesistono nello stesso istante temporale. È utile perchè teniamo conto di un unico documento di requisiti per le versioni

![[Pasted image 20250609165653.png]]

Bisogna arrivare al cambiamento preparati, non subirlo, quindi é consigliato sviluppare requisiti facilmente modificabili. Il cambiamento può portare:
- costo elevato per risolverlo
- impatto sul sistema

Per rispondere al meglio quindi bisogna identificare i punti o i requisiti che con probabilità facilmente cambieranno, uno dei modi per farlo è classificare i requisiti per probabilità di cambiamento, associando un livello di stabilità ai requisiti che ne rientrano

![[Pasted image 20250609170722.png]]


---
### Tracciabilità e gestione per il supporto all’evoluzione

Bisogna esplicitare la tracciabilità dei requisiti, ovvero un requisito (o qualsiasi elemento del documento) è tracciabile quando siamo in grado di capire il motivo per cui è stato scritto:

- da dove viene
- perchè è li
- per cosa verrà usato
- e come sarà usato

è necessario quindi avere dei link di tracciabilità per un requisito, ripercorrere all'indietro l'origine di un requisito ci permette di valutare le motivazioni e decidere se è ancora valido o non.

Anche perchè certi requisiti sono le basi o fondamentali per altri requisiti che lo richiedono

 Il cambiamento potrebbe avere un impatto anche su diagrammi legati al documento dei requisiti, perciò è necessario che anche questi siano modificati. Il cambiamento ha due dimensioni: 
 - Orizzontale: ha impatto sullo stesso dominio di applicazione. 
 - Verticale: ha impatto su un dominio di applicazione diverso (componenti architetturali, codice, . . . ).
La tracciabilitlò puè essere:
- All’indietro backward: per risalire alle motivazioni. 
- In avanti: forward: per capire l’impatto di un cambiamento.

![[Pasted image 20250609172505.png]]


---
### Tassonomia dei link di tracciabilità

I link di base sono di dipendenza:

![[Pasted image 20250609173125.png]]

e poi si suddividono in 
- inter versione (tra versioni differenti)
	- link variante
		![[Pasted image 20250609173446.png]]
	- link revisione
		![[Pasted image 20250609173654.png]]
- intra versione (stessa versione)
	- link usabilità
		![[Pasted image 20250609174103.png]]
	- link derivazione
		![[Pasted image 20250609174114.png]]


---
### Soddisfacilità

possiamo diere che i requisiti del sitema sono soddisfatti quando

![[Pasted image 20250609182200.png]]


---
### Processo di tracciabilità dei cambiamenti

Dobbiamo adottare un sistema di gestione della tracciabilità, che introduce un costo nella realizzazione del progetto in termine di manutenzione ed effort
![[Pasted image 20250609183549.png]]
2. Stabilire link di tracciabilità
	Bisogna definire la policy dei link, ovvero stabilire:
	- il livello di granularità dei link che vogliamo propagare
	- indicare quali dati associare ad ogni link
	- specificare i tipi dei link
	Questo produce il grafo della tracciabilità
3. Documentare i link di tracciabilità
	I link possono essere percorsi in:
	- avanti: quando devo valutare l'impatto di un cambiamento di un requisito
	- indietro: per valutare le motivazioni dei requisiti
	inoltre sono utili per:
	 - analisi di copertura
	 - supporto alla documentazione dei requisiti perch´e permettono di identificare le dipendenze quando discutiamo o ridefiniamo un requisito. Verificando l’impatto di qualche modifica
4. Per utilizzare i link di tracciabilità, essi devono essere mantenuti in caso di cambiamento e quindi è opportuno che siano corretti 

---
### Metodologie di tracciabilità

- [[cross referencing]]
- [[matrici di tracciabilità]]
- [[liste di tracciabilità]]
- [[diagramma di funzionalità]]
- [[Database di tracciabilità]]


---
### Generatori di link di tracciabilità

esistono vari modi automatizzati per identificare i link, alcune cosistono in information retrieval, utilizzando delle keyword. Vanno a vedere la similirità tra le parole contenute in item e qualora ci fossero item con requisiti oppure componenti del documento dei requisiti con keyword simili, il sistema propone un link

![[Pasted image 20250610101010.png]]
potrebbero perdere alcuni link

L'obiettivo è raggiungere un **equilibrio ottimale** tra:

- **Costo**: creazione e mantenimento del grafo di tracciabilità.
- **Benefici**: supporto all’evoluzione del software, analisi delle motivazioni (rationale), analisi di copertura, gestione dei difetti, ecc.

Questo porta al problema del *Delayed Gratification* nel senso che si cerca di risolvere sul momento per avere benefici nel futuro anche da parte di altri, Questo crea **resistenza iniziale** all’investimento nella tracciabilità.

Per risolvere serve una **politica di tracciabilità specifica al progetto**, che:

- Controlli efficacemente i **parametri in uscita** (es. qualità dei link, benefici ottenuti),
- a partire da **parametri in ingresso** (es. dimensione del progetto, requisiti, criticità).

Le fasi principali del ciclo sono
![[Pasted image 20250610102537.png]]

Per definire la policy devo mettere in conto certi aspetti:
- **Dimensione del progetto**: più è grande, maggiore il bisogno di tracciabilità.
- **Distribuzione fisica e turnover del team**: maggiore dislocazione/ricambio = più bisogno di chiarezza sui legami tra requisiti.
- **Tempistiche strette**: meno tempo → meno peso possibile sulla tracciabilità.
- **Durata prevista del software**: più lunga → più utile investire in tracciabilità.
- **Vincoli imposti da clienti/agenzie**: se richiedono tracciabilità esplicita, la politica deve adeguarsi.
- **Numero stimato di requisiti/assunzioni da tracciare**: più elementi → più necessità di automazione.
- **Proporzione di requisiti critici per la missione**: più sono, più importante è la tracciabilità.
- **Proporzione di requisiti volatili (soggetti a cambiamenti)**: alti livelli di volatilità → maggiore tracciabilità utile per gestire il cambiamento.

Dopo questo si intavola una discussione per capire il livello a cui spingersi della gestione formale dei link, visti più o meno  nel processo di tracciabilità dei cambiamenti


---
### Change control

![[Pasted image 20250610103718.png]]
1. **Inizializzare il cambiamento**:
	Il processo parte con l’identificazione del cambiamento, che può accumulare richieste di cambiamento sia da membri del team che da esterni. I cambiamenti possono essere: 
	- Correttivi: correggere errori.
	- Adattivi: adattare il sistema a nuove condizioni.
	- Migliorativi: migliorare il sistema.
	Deve essere menzionato il livello di urgenza del cambiamento, e il livello di impatto sul sistema
2. **Valutazione e priorizzazione del cambiamento**:
	Le richieste si accumulano in una wishlist che viene discussa, spesso da una board indipendente di revisione, quindi dagli stakeholders, esperti di dominio e utenti finali. Devono essere elencate i vantaggi e gli svantaggi dei cambiamenti.
	Il risultato è il raggiungimento di un accordo se adottare il cambiamento o no
3. I cambiamenti vanno in consolidamento, quindi le modifiche vengono integrate e scaturiscono una nuova versione del documento dei requisiti o una versione del sistema