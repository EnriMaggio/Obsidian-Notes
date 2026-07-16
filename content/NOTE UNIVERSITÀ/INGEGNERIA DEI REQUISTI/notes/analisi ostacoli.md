 Giocare in anticipo per quanto riguarda contranstare gli ostacoli permette di avere un diagramma dei goal più realistico e più completo (verranno aggiunti goal appositi per mitigare i vari ostacoli).

dovremo quindi
- identificare quanti più ostacoli possibili
- definire la probabilità e la severità delle conseguenze
- ideare una possibile soluzione
- elaborare una rimodellazione dei goal

è un processo prettamente iterativo fin quando non si raggiunge un punto fisso

![[Pasted image 20250424140553.png]]

Una buona prassi è quella di partire dai nodi foglia del diagramma dei goal, questo perchè i goal ai nodi foglia sono i più elementari e quindi più semplici da sviluppare una soluzione.

Ci si ferma quando si ha finto di analizzare i goal più critici e quando certe conseguenze che possono avvenire vengono ritenute accettabili in termini di severità

---
### Identificazione ostacoli

per prima cosa si parte dai goal di alto livello, il primo step è identificare i root obstacle, ovvero gli ostacoli che impediscono il raggiungimento di quei goal. È Sempre la negazione dello stesso goal

![[Pasted image 20250611113326.png]]

Si procede poi con la AND-decomposition e la OR-decomposition per identificare tutte le possibili cause di quel root obstacle, fin tanto che non si raggiungono ostacoli atomici.

![[Pasted image 20250424141303.png]]


![[Pasted image 20250424141506.png]]
Si va ad invertire la proprietà di dominio
![[Pasted image 20250424141613.png]]
andiamo a vedere come avvengono questi ostacoli appena inseriti raffinando quest'ultimi
	
![[Pasted image 20250424141731.png]]
![[Pasted image 20250424141856.png]]

---
### Pattern per identificare gli ostacoli

Ad esempio con un mantain goal l'ostacolo principale è la mancanza di persistenza in un certo punto del tempo del mantain goal stesso

![[Pasted image 20250424143225.png]]

Con un achieve goal è simile l'identificazione dell'ostacolo

![[Pasted image 20250424143356.png]]


---
### Valutare gli ostacoli

Per valutare gli ostacoli abbiamo bisogno grande conoscenza del dominio.  Solitamente, si coinvolgono degli esperti di dominio in cui si lavora, in modo da capire la probabilità di occorrenza e l’impatto di questi ostacoli.

Un modo per ragionare per calcolare la probabilità di un ostacolo è quella di misurare sempre la probabilità, ma del massimo dei sotto ostacoli relativo a quello in caso di or e minimo in caso di and

![[Pasted image 20250424144132.png]]

---
### Risoluzione ostacoli

Principalmente consiste nel creare nuovi goal come contromisure che permettono di mitigare l'ostacolo. Questi goal vengono collegati all’ostacolo tramite un link di risoluzione.

ovviamente ci sono più soluzioni e modi differenti per risolvere gli ostacoli e bisogna valutare la migliore in termini di costi,benefici e rischi

![[Pasted image 20250424144430.png]]


---
### Metodi per risolvere gli ostacoli

- **Sostituzione del goal**: 
	nel caso in cui nel goal top-level ci siano diverse alternative per raggiungere il goal, si possono esplorare queste alternative per capire quale sia la 
	migliore anche in termini di rischi, ovvero si possono sceglire alternative meno rischiose che non presentato ostacoli. Se una delle alternative contiene un rischio rispetto ad un’altra, allora si può considerare di scartare questa alternativa.
	
	![[Pasted image 20250424144748.png]]

- **Sostituzione di agente**: 
	in certe situazioni potrei trovarmi di fronte alla necessità di rivedere l’agente utilizzato per raggiungere il goal, in quanto potrebbe rimuovere la presenza di un ostacolo.
	
	![[Pasted image 20250424145036.png]]

- **Indebolire il goal**:
	se il goal, così come è stato definito, è troppo difficile da raggiungere (troppo ideale), si può considerare di indebolire il goal, in modo da renderlo più facile da gestire e da raggiungere.
	
	![[Pasted image 20250424145746.png]] 
- **Prevenzione di ostacoli**: 
	definire un goal che cerca di porre rimedio ad un ostacolo. Lo si fa in modo diretto quindi si utilizza un *avoid [obstacle]*. Parte dalla negazione dello stesso goal
	
	![[Pasted image 20250611115456.png]]

- **Ripristino di goal**:
	si rafforza la condizione target quando occore l'ostacolo
	 ![[Pasted image 20250611115911.png]]
	
- **Riduzione di ostacoli**: 
	definiamo tecnicamente un nuovo goal che cerca di rimediare un singolo ostacolo di basso livello.
	
	![[Pasted image 20250611120044.png]]

- **Mitigazione di ostacoli**
	introduciamo nuovi goal per mitigare le conseguenze(effetti dannosi) di un ostacolo. Distinguiamo quindi due diverse strategie di mitigazione di ostacoli:
	
	 - **Mitigazione debole**: accettare l’ostacolo e ridefinire il goal in modo tale che una versione più debole dello stesso goal venga realizzata.
		![[Pasted image 20250611120326.png]]
	
	 - **Mitigazione forte**: si ripristina il goal di alto livello in caso di ostacoli che ostruiscono i goal di basso livello
	 ![[Pasted image 20250611120457.png]]
	una volta mitigati devono essere ulteriormente raffinati



