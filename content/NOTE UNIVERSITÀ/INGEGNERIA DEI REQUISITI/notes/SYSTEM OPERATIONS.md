Per operazione intendiamo cosa fa il sistema per raggiungere i goal e come vengono rappresentate le operazioni.

Le operazioni riguardano le operazioni attive, ovvero le azioni che il sistema deve compiere per raggiungere i goal.

---
### Operation model

si tratta di una vista funzionale del sistema modellato in termini di:
- serivizi forniti
- servizi dispiegati sotto varie condizioni per il soddisfaccimento dei goal

La rappresentazione avviene sempre mediante l’ausilio dei diagrammi UML declinati in maniera funzionale alla modellazione dei requisiti.

Gli obiettivi di tale diagramma sono molteplici, tra cui:

- Fornire un input agli sviluppatori per la specifica del software.
- Descrivere le procedure e i task all'interno dell'ambiente.
- Può essere un punto di partenza per identificare con quali dati interagirà il sistema o essere l'input per i tool di prototipazione o animazione dei requisiti.Si possono già creare i primi test di accettazione
- Possiamo utilizzarli per stimare i _function point_, ovvero capire quanto lavoro ci sarà da fare per l'implementazione delle varie componenti.
- Permette di creare un link tra tutte le funzionalità del sistema e i goal che si vogliono raggiungere.


---
### Cosa sono le operazioni

le operazioni sono una mappatura da stato di input a stato di output, ovvero una operazione è una coppia di stati del sistema, di input e di output, e con l'operazione stessa si può cambiare lo stato del sistema. Le operazioni possono cambiare i valori degli attributi

- **Operation** Op = set di coppie di stati input-output (relazione binaria)
    - Op ⊆ InputState × OutputState
    - **state** = tupla di coppie funzionali xi​ → vi​ (cfr. conceptual object lecture)
        - xi​: variabile, vi​: valore corrispondente
    - **input variables**: rappresentano i dati che il sistema riceve in input per poter eseguire un’operazione.
    - **output variables**: rappresentano i dati che il sistema restituisce in output dopo aver eseguito un’operazione.
    - **attributes** di variabili i/o istanziate come variabili di stato
- **Operation applications** producono transizioni di stato (eventi)

![[Pasted image 20250612154900.png]]

La transizione avrà degli effetti sulle variabili e in generale dal sistema, quest'ultimo dovrà controllare l'evoluzione del salto

l'operazione infine operazionalizza i goal del goal model, in modo da poterli soddisfare e che viene raggiunto. È il modo in cui gli agenti modificano l'ambiente per raggiungere gli obiettivi

Le operazioni possono essere:

- Generalmente deterministici: la relazione sugli stati è una funzione.
    - non ci sono output alternativi multipli dallo stesso input.
- Atomiche: mappa lo stato di input allo stato all'unità di tempo più piccola successiva.
    - non decomponibile in operazioni a grana più fine.
    - decomponi i goal sottostanti, non le operazioni! (semanticamente più semplice).
    - per operazioni che durano per una certa durata: usa eventi startOp/endOp.
- Può essere applicato contemporaneamente ad altri.
    - concorrenza intra-agente (oltre alla concorrenza inter-agente).
    - ad esempio, OpenDoors || DisplayWhichPlatform.
- Operazioni software, operazioni ambientali (tasks).
    - ad esempio, PlanMeeting, SendConstraints.



---
### Come è fatto una operazione

le operazioni hanno:
- nome
- definizione
- categoria
- firma che dichiara la relazione di input e output sugli stati

Ci sono due modi per rapprenentarli
![[Pasted image 20250612155630.png]]


---
### Pre e post condizioni di Dominio

un'operazione può avvenire sotto certe conzioni:
- DomPre:
	caratteristiche all'interno del dominio che sono necessarie, vere per abilitare la operazioni
- DomPost:
	quali sono le condizioni che caratterizzano l'avvenuta l'operazione, ovvero cosa è cambiato nel dominio, insomma capire le condizioni con cui è possibile capire se l'operazione è stata eseguita in modo corretto

sono degli statment descrittivi

![[Pasted image 20250612160247.png]]

C'è di fatto un link tra operazione, agente e goal. è importante avere consistenza, cioè ogni variabile di input e di output devono obbligatoriamente essere tra le variabili controllate/monitorate dall'agente, inoltre ogni operazione deve essere attivata da un solo agente 


---
### Operalizzazione dei goal

La metodologia goal oriented permette di operazionalizzare i leaf goal, e questo è il motivo primario per cui abbiamo la destrutturazione dei goal di alto livello in goal di basso livello.

Le condizioni in questo caso sono prescrittive, quando il link di operalizzazione collega goal e operazione

-  ReqPre: le condizioni necessarie affinchè l’operazione possa soddisfare il goal (abilitano il permesso di fare l'operazione). 
- ReqTrig: le condizioni sufficienti affinchè l’operazione possa soddisfare il goal (è una condizione/evento per far scattare l'operazione). 
- ReqPost: le condizioni che devono essere verificate affinchè l’operazione abbia soddisfatto il goal.


![[Pasted image 20250612161119.png]]
![[Pasted image 20250612161821.png]]

Generalmente un leaf goal è operazionalizzato da più operazioni, e delle operazioni possono operazionalizzare più leaf goal.

Quando succede, tutte le precondizioni e le postcondizioni devono essere implicitamente congiunte (in and). Se una precondizione di dominio è  vera, deve essere applicata appena la condizione di trigger diventa vera. Se una precondizione di dominio può essere applicata quando tutte le condizioni di operalizzazione sono vere.

![[Pasted image 20250612162213.png]]


---
### Impegno degli agenti

Un agente ha la responsabilità di raggiungere uno o più goal e ha le operazioni per poterlo fare.

Aabbiamo che l’agente deve garantire che l’operazione sia applicata, quindi per ogni goal che l'agente è responsabile e per ogni sua operazione deve garantire l'applicazione:
- Quando le operazioni DomPre sono vere
- Appena le operazioni ReqTrig diventano vere.
- Solo se le operazioni ReqPre sono vere
- In Modo tale che le operazioni DomPost e ReqPost siano vere.

Questo è quello che deve fare l'agente

ci sono due strategie che ogni agente può intraprendere:
 - Eager: l’agente fa partire l’operazione non appena le condizioni ReqPre sono vere.
 - Lazy: l’agente aspetta che le condizioni ReqTrig siano vere, quando si trova costretto.

Gli agenti possono essere concorrenti, possono far partire operazione in maniera asincrona/parallelo, anche tra agenti diversi

![[Pasted image 20250612163653.png]]



---
### Rappresentazione semantica

![[Pasted image 20250612164010.png]]
è una serie di transizione di stati nel tempo, le successioni possono avvenire in parallelo

![[Pasted image 20250612164209.png]]


---
### Use case diagram

c'è un altro modo per rappresentare il diagramma delle operazioni, ed è attraverso un use case UML diagram che rappresenta:
- l'agente con tutte le sue operazioni
- relazioni con altri agenti

Ci sono dei link tra le operazioni di extend e include.
- Include: l’operazione include un’altra operazione se quest'ultima è verificata e fatta prima dell' altra operazione(è obbligatoria). Non è una decomposizione 
- Extend: viene usato per eitchettare dipendenze che si attivano quando una operazione ha un effetto eccezionale.

Dobbiamo però ricordarci che le operazioni sono atomiche, non decomponibili in sotto operazioni, perciò questa tipologia di link non sarebbe da utilizzare.

![[Pasted image 20250612164634.png]]

Lo scope del diagramma documenta l'agente e le sue operazioni che stiamo affrontando

![[Pasted image 20250612164900.png]]


---
### Euristiche per l'operation diagram

- goal fluents:
	i fluents non sono altro che condizioni che definiscono l’avvio o il termine di una qualche operazione. Permettono di modellare il concetto di flusso per una successione di operazioni
	
	![[Pasted image 20250612165640.png]]
- Possiamo utilizzare le interazioni all’interno degli scenari. Gli scenari possono essere metodologie per l’espressione dei requisiti.
	
	![[Pasted image 20250612170508.png]]

- Rafforzamento delle precondizioni e postcondizioni con condizioni richieste dagli obiettivi
	- **dentificare i permessi richiesti**: se l'effetto DomPost di un'operazione può violare un obiettivo G sotto condizione C
	    - ReqPre per G: non C
	    - es. OpenDoors: ReqPre per "Moving → Closed": non Moving
	- **Identificare le obbligazioni richieste**: se l'effetto DomPost di un'operazione è prescritto da un obiettivo G da mantenere ogni volta che la condizione C diventa true
	    - ReqTrig per G: C
	    - es. OpenDoors: ReqTrig per "StoppedAtPlatform → Open": StoppedAtPlatform
	- **Identificare gli effetti aggiuntivi richiesti**: se il DomPost di un'operazione non è sufficiente per garantire la condizione target T di un obiettivo G
	    - ReqPost per G: condizione mancante da T (devo aggiungerlo al domPost)
	    - es. PlanMeeting: ReqPost per ConvenientMeeting: data non in date escluse
- disegnare l'use case diagram dato i requisiti
	
	![[Pasted image 20250612171218.png]]