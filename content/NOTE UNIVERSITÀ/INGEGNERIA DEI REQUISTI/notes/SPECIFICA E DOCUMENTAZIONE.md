> L'obiettivo di questa sezione è scrivere il documento dei requisiti

adesso si può incominciare a fare la stesura del documento dei requisiti
documentare significa quindi catturare i requisiti e descriverle in 3 punti:

- Definizione precisa di tutte le caratteristiche
	Comprende gli obiettivi, i concetti, le proprietà del dominio rilevanti, i requisiti del sistema, le ipotesi e le responsabilità.
- Razionale delle opzioni adottate
	Motivazione delle scelte effettuate e argomentazioni per la soddisfazione dei requisiti
- Evoluzioni e varianti del sistema 
	Discussione sulle possibili evoluzioni e varianti del sistema previste nel tempo



---
### testo libero

La prima modalità è quello di descrivere il documento con linguaggio naturale di tutto quello che si è stabilito nelle sezioni precedenti 

![[Pasted image 20250606095435.png]]
(per ambiguità si intende che una fase è interpretata in diversi modi da più persone)

Ci sono delle linee guida per evitare degli errori nella scrittura del documento per strutturare il contenuto in maniera completa e comprensibile

Regole stilistiche per una buona specifica in Linguaggio Naturale (LN):

- Identifica chi leggerà questo documento, quindi identificare il background di chi legge.
- Dì cosa farai prima di farlo, ovvero creare una piccola sintesi prima di partire con i dettagli.
- Motiva prima, riassumi dopo.
- Assicurati che ogni concetto sia definito prima dell'uso.
- Continua a chiederti: "È comprensibile? È sufficiente? È rilevante?".
- Mai più di un requisito, un'assunzione o una proprietà di dominio in una singola frase. Mantieni le frasi brevi, dare concetti per ogni frase.
- Usa "deve" per le prescrizioni obbligatorie, "dovrebbe" per quelle desiderabili.
- Evita gergo e acronimi non necessari e se in caso vengono usati è necessario fornire una spiegazione.
- Usa esempi suggestivi per chiarire affermazioni astratte.
- Fornisci diagrammi per relazioni complesse tra gli elementi.
- spesso è funzionale aggiungere una tabella decisionale che spiega un po' il funzionamento del sistema nel caso di complesse combinazioni di condizioni
	![[Pasted image 20250606101315.png]]
	Questo approccio assicura una completa verifica e un’integrazione logica delle condizioni di input e output, in questa tabella ci si può accorgere se avvengono delle ottimizzazioni. Nell'esempio la prima e la terza colonna possono riunite in una sola, visto che hanno gli stessi output.
	Questa fase di tabulazione può essere d'aiuto nella creazione di test di accettazione
	![[Pasted image 20250606102058.png]]
	![[Pasted image 20250606102108.png]]


---
### Consigli per i Template: Componenti Essenziali per Affermazioni Standardizzate


I template standardizzati sono cruciali per la formulazione e l'organizzazione della documentazione dei requisiti nei progetti.

Componenti principali di un template standard per le affermazioni:

- **Identificatore:**
    - Assegna un nome intuitivo e, se necessario, gerarchico all'affermazione.
    - Facilita la ricerca e il riferimento incrociato tra affermazioni correlate.

- **Categoria:**    
    - Classifica l'affermazione (es. requisiti funzionali/di qualità, assunzioni, proprietà del dominio, definizioni, esempi di scenario).
    - Aiuta a organizzare le affermazioni in modo logico.

- **Specifica:**
    - Dettaglia la formulazione dell'affermazione.
    - Seguire regole stilistiche precise per chiarezza e precisione.

- **Criterio di Adeguazione:**
    - Fornisce criteri per misurare o verificare l'affermazione.
    - Essenziale per la validazione e il controllo qualità.

- **Fonte:**
    - Indica la provenienza dell'affermazione.
    - Garantisce la tracciabilità, collegandola ad evidenze o requisiti originali.

- **Razionale:**
    - Spiega il motivo alla base dell'affermazione.
    - Migliora la comprensione e facilita la tracciabilità.

- **Interazione:**
    - Descrive come l'affermazione interagisce con altre affermazioni.
    - Include potenziali contributi o conflitti.
    - Essenziale per la gestione delle dipendenze.

- **Livello di Priorità:**
    - Stabilisce un livello di priorità per l'affermazione.
    - Aiuta nella gestione delle risorse e nella pianificazione del progetto.

- **Stabilità, Livelli di Comunalità:**    
    - Supportano la gestione del cambiamento.
    - Valutano l'applicabilità dell'affermazione su diverse applicazioni o progetti.

un altra regola è quello di avere un criterio che trasforma requisiti generici in requisiti misurabili per facilitare la decisione se un requisito è stato raggiunto o meno dal sistema implementato. Viene utilizzato particolarmente con i requisiti non funzionali

![[Pasted image 20250606102955.png]]

È anche un modo per mettersi d'accordo con gli stakeholder.

La documentazione deve seguire regole globali per la strutturazione dei documenti di requisiti organizzati, raggruppando elementi simili come obiettivi del sistema, componenti, e caratteristiche del software per capitoli. Questo aiuta a mantenere la documentazione organizzata e facilmente navigabile

si può seguire lo [[standard IEEE std-830]]


---
### Uso delle notazioni Diagrammatiche

ovviamente utilizza un linguaggio non naturale, ma un linguaggio grafico. Con i diagrammi non si riesce in toto a comprendere tutte le sfacettature, ma sono abbastanza comodi. Si può dire che sono semi-formali.

I diagrammi sono:
- [[diagrammi entità relazioni]]
- [[diagrammi sadt]]
- [[diagrammi dataflow]]
- [[diagramma casi d'uso]]
- [[diagramma traccia eventi]]
- [[diagramma state machine ]]
- [[diagramma statechart]]

Avendo a disposizione una varietà di diagrammi per rappresentare i requisiti del sistema, possiamo integrare i diversi diagrammi dato che ciascuno fornisce una prospettiva unica sul sistema.

Una prima verifica, data dai sistemi automatici, può essere fatta per verificare la consistenza tra i diagrammi. Le inconsistenze che si possono verificare possono essere diverse, tra cui:
- tutti i componenti di un problem diagram devono essere presenti in un diagramma entità-relazione. 
-  tutti i fenomeni di un problem diagram devono essere presenti in un diagramma entità-relazione come un’entità, un attributo o una relazione.

Ci sono viste alternative in UML che ci permetto di ragionare, non tanto sull’architettura, ma supportano nella fasi di progettazione e validazione dei requisiti, come ad esempio:
- Diagrammi delle Classi: utili per la vista strutturale del sistema. 
- Use Case Diagram: utile per la vista operazionale del sistema.
- Sequence Diagram: utile per la visione degli scenari.
- State Diagram: utile per la visione delle state machine.

![[Pasted image 20250606140835.png]]

UML fornisce una buona base di partenza per lo sviluppo dei requisiti

![[Pasted image 20250606141202.png]]