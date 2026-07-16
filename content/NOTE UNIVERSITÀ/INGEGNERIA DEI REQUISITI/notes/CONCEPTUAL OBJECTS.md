Intendiamo una vista strutturale del sistem to-be che vogliamo modellare o il sistema attuale che vogliamo analizzare (as-is)

Il linguaggio utilizzato è l'UML diagram, che tratterà oggetti non nel senso di programmazione informatica, ma che rappresentano elementi del nostro dominio. Per questo motivo le classi non avranno operazioni, solo attributi.

serve quindi per:
- documentare il sistem as-is e to-be
- fissare un vocabolario
- fornisce una base per il goal diagram

c'è una leggera differenza per come vengono trattati gli oggetti nella nostra metodologia

![[Pasted image 20250611151118.png]]
---
### Oggetto concettuale

![[Pasted image 20250611151002.png]]

Per stato si intende una coppia (nome,valore)

![[Pasted image 20250611151515.png]]

La relazione tra oggetti e le istanze degli oggetti è marcata/stabilità con la relazione esplicita *InstanceOf(o, obj)* se e solo se un object instance è un'instanza di un oggetto, le istanze di oggetto possono cambiare relazione con altri oggetti, cioè possono essere istanze di altri oggetti

![[Pasted image 20250611151908.png]]

Nella rappresentazione diagrammatica, per ogni oggetto bisogna specificare obbligatoriamente la motivazione per cui un’istanza è istanza di un oggetto,attraverso delle notazioni di definizione, che specificano le condizioni necessarie e sufficienti per un instanza di oggetto essere istanza di un oggetto

---
### Tipi di oggetti concettuali

- [[entità]]
- [[associazioni]]
- [[evento]]
- [[agente]]

![[Pasted image 20250611152955.png]]

---
### Attributi

![[Pasted image 20250611155218.png]]

Gli attributi possono essere:
- elementari: valori atomici
- strutturati: valori con una certa struttura
- precisi
- molteplicità
	![[Pasted image 20250611155507.png]]


---
### Eurostiche per modellare gli oggetti concettuali

Nel processo di modellazione degli oggetti, è fondamentale seguire determinate euristiche per assicurare una progettazione chiara e funzionale. Di seguito sono elencate le principali linee guida da considerare

- **Revisione delle Specifiche**
	È cruciale rivedere tutte le specifiche degli obiettivi e delle proprietà del dominio contenute nel modello degli obiettivi per garantire che tutte le necessità siano adeguatamente rappresentate e comprese. Comodo da fare dopo la creazione del goal diagram
	![[Pasted image 20250611161826.png]]
- **Assegnazione degli Obiettivi**: Per l'implementazione degli obiettivi nel software da realizzare, è essenziale introdurre rappresentazioni condivise degli oggetti dell'ambiente riferiti dagli obiettivi.
	![[Pasted image 20250611162046.png]]
- **Definizione degli Attributi**: Un elemento è da considerare un attributo se è una funzione che restituisce un valore unico, le sue istanze non necessitano distinzione, non si prevede di aggiungervi attributi o associazioni, e non si intende specializzarne l’intervallo di valori
	![[Pasted image 20250611162722.png]]
- **Oggetti Concettuali negli Obiettivi:**
    - Gli oggetti concettuali definiti da uno stato unico (esempio: _StartTrain_) implicano eventi.
    - Gli oggetti che attivano e controllano comportamenti di altre istanze (esempio: _DoorsActuator_) agiscono come agenti.
	    ![[Pasted image 20250611162928.png]]
- **Attributi nelle Associazioni:** Un attributo deve essere collegato a un'associazione se caratterizza tutti gli oggetti partecipanti, sia esplicitamente che implicitamente.
- **Link Strutturali e Associativi:** Considerare la creazione di un'associazione se esiste un link strutturale tra oggetti compositi e componenti che soddisfa specifiche condizioni operative o strutturali.
- **Specializzazioni e Generalizzazioni:** È importante identificare specializzazioni e generalizzazioni attraverso l'analisi di attributi comuni, associazioni e invarianti di dominio, contribuendo alla creazione di un modello più organizzato e scalabile.

---
### errori da evitare

- **Uso di Associazioni invece di Puntatori:** 
	Evitare l'utilizzo di "puntatori" agli altri oggetti come attributi e preferire l'uso di associazioni binarie.
	![[Pasted image 20250611163538.png]]
- **Nomi e Definizioni Chiare:** Utilizzare nomi suggeriti e chiari per oggetti e attributi, evitando ambiguità e assicurando una definizione precisa e dettagliata.
	![[Pasted image 20250611164139.png]]

