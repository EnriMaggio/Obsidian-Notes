il diagramma dei goal va a coprire la dimensione del perchè e come un goal viene realizzato all'interno di un sistema

il diagramma è composto da:
- nodi: goal rappresentati con un parallelogramma
- archi: specificano l'orientamento

![[Pasted image 20250610170046.png]]

I goal Possono avere delle annotazioni per specificare ulteriori attributi di questo goal, e possono avere delle precise definizioni a seconda del progetto software

![[Pasted image 20250610170142.png]]


---
### Raffinamento dei goal 

Un goal di alto livello può essere raffinato in più goal di basso livello per poterlo realizzare e può essere di due tipi:
- AND
	![[Pasted image 20250610170537.png]]
	è necessario che tutti i sotto-goal siano soddisfatti contemporaneamente, ed è una condizione necessaria per il raggiungimento del goal di più alto livello
	![[Pasted image 20250610170914.png]]
	
- OR REFINEMENT
	ci permettono di catturare goal alternativi per raggiungere il goal di alto livello, quindi ci sono modi differenti con cui raggiungere il goal, da non confondersi con l'or operatore logico
	![[Pasted image 20250610173423.png]]
- OR ASSIGNMENT
	È la stessa cosa soltanto che qua specifichiamo le alternative dei possibli agenti che possono avere la responsabilità su un goal
	![[Pasted image 20250610173914.png]]



---
### Proprietà di dominio

A volte i goal non sono sufficienti a garantire per raggiungere quelli di alto livello e quindi si ha bisogno di aggiungere informazioni di dominio che possono essere:
- Invariante di dominio: proprietà di dominio che non varia, sempre vera.
- Ipotesi di dominio: proprietà che sono assunzioni

ad esempio
![[Pasted image 20250610171316.png]]

In presenza di raffinamento and dei goal insieme alle proprietà di dominio, si  devono rispettare due proprietà:
	- Consistenza: i goal e le proprietà non sono contradittorie
		![[Pasted image 20250610171531.png]]
	- Minimalità: il sottoinsieme dei goal deve essere minima, cioè se si toglie uno il goal di alto livello non verrebbe raggiunto
		![[Pasted image 20250610171633.png]]

![[Pasted image 20250610174543.png]]

---
### Alberi di raffinamento 

l'albero di raffinamento si espande e finisce con i nodi foglia che rappresenteranno i requisiti perchè saranno collegati con singoli agenti. Significa che i nodi foglia sono stati responsabilizzati da un agente

![[Pasted image 20250610171904.png]]

Seguendo i goal si va in giù per capire come realizzare quel goal e andando verso sù si capisce il perchè/la motivazione di raggiungere goal di alto livello

Il grafo diagramma sarà composto infine


- **Radici (roots)** = Obiettivi di alto livello del sistema:
    - Possono essere **funzionali** o **non funzionali**
    - Possono essere **comportamentali (behavioral)** o **soft (qualitativi)**
        
- **Foglie (leaves)** = Requisiti o aspettative:
    - Sono **assegnabili a singoli agenti**

- **AND-refinement**:
    - Collega un obiettivo padre a un insieme di **sotto-obiettivi congiunti**
    - Tutti i subgoal devono essere soddisfatti
    
- **OR-refinement**:
    - Collega un obiettivo padre a un insieme di alternative (ognuna un AND-refinement)
    - Rappresenta **opzioni alternative del sistema**
    - Gli **obiettivi soft** aiutano a selezionare l’opzione preferita
        

- È generalmente un **grafo diretto aciclico (DAG)**, **non un albero**
    - Possono esserci **più radici** (es. obiettivi funzionali e non funzionali)
    - Un obiettivo può contribuire a **più obiettivi genitori**


---
### Potenziali conflitti

ci possono essere dei legami diversi tra i goal, ovvero può essere che certi goal sono contrastanti tra di loro e questo può portare a contributi negativi nel sistema

![[Pasted image 20250610172554.png]]

Quando ci si accorge del conflitto bisogna solo segnalarlo, non risolverlo subito


---
### Annotazione Goal

spesso è opportuno aggiungere note ai goal per capire le origini e le motivazioni di certe scelte. Di solito viene utilizzato per capire l'origine di ogni dipendenza

![[Pasted image 20250610174942.png]]


---
### Euristiche per l’individualizzazione dei goal

Quali goal dobbiamo andare a documentare, esistono delle euristiche e dei pattern da seguire.

-  Analizzare gli obiettivi correnti del sistema as-is.
	perchè i goal del sistem as-is sono simili e ad alto livello rispetto a quelli del system to-be
- Cercare keyword all’interno del materiale elicitato (doumento dei requisiti ecc.ecc.)
	 Le keyword suggeriscono alla presenza di goal e possono essere intenzionali, prescrittivi o migliorative. Non solo è utile per i goal ma anche per il raffinamento dei goal stessi
- Cercare all’interno delle tassonomie di goal
	Questo per capire più che altro quali tipologie di goal sono presenti all'interno del nostro sistema, e potrebbero far emergere dei goal non specificati esplicitamente prima rispetto ad una certa categoria
- Astrazione Bottom-up:
	capire la motivazione del perchè un goal è stato introdotto
- raffinamento top-down:
	come un goal viene soddisfatto
![[Pasted image 20250610180233.png]]
- Utilizzare gli scenari.
	![[Pasted image 20250610180329.png]]
- Dividere le responsabilità tra gli agenti.
	![[Pasted image 20250610180725.png]]
- Identificare i goal pro e contro in base alle alternative. Mi permette di capire quali potrebbero essere i soft goal
	![[Pasted image 20250610182520.png]]
- Dagli Achive goal posso identificare i Maintain goal, perchè spesso compaiono entrambi 
- capire lo scope dei goal, quando fermarci nel raffinamento di un goal
- Non confondere i goal con le operazioni (errore tipicamente frequente nei nodi foglia)
	![[Pasted image 20250610183434.png]]
	![[Pasted image 20250610183837.png]]
- Non confondere AND-refinement con OR-refinement.
	![[Pasted image 20250610184041.png]]
- Evitare ambiguità.


---
### Pattern ricorrenti

ci sono dei pattern interessanti che ci pongono se alcuni goal sono impliciti e quindi si andrà ad esplicitarli

catturano tattiche di elicitazione che ci guidano nella modellazione e nell'identifcazione di goal e anche di legami fra i vari goal

possibili pattern:
- MileStone: 
	in presenza di current condition e target condition abbastanza contrastanti, utile per goal impliciti che hanno bisogno di condizioni intermedie per raggiungere il goal
	![[Pasted image 20250611102334.png]]
- Per casi distinti:
	ovvero elencare quali sono tutti i casi con cui si riesce ad arrivare alla condizione target
	![[Pasted image 20250611102839.png]]
- guardie:
	Quando si ha la necessità di verificare una guardia/condizione per raggiungere la condizione target
	![[Pasted image 20250611103058.png]]
- dividi et impera:
	quando in un mantain goal, c'è la pressenza and di GoodCondition
	![[Pasted image 20250611103219.png]]