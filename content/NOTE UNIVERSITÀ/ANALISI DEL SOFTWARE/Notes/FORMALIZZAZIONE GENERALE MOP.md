#### :LiCalendarClock:  12/11/2024 - 09:28

#### Formalizzazione generale

Ora verrà definita la soluzione generale MOP al di fuori delle available expression

Gli ingredienti della nostra soluzione sono:

- costruzione del CFG
- $D$ insieme de i dati osservati, ovvero un reticolo completo
- $d_0 \in D$ informazione iniziale di partenza dell'analisi (entry o exit se analisi FW o BW)
- una funzione $f$ monotona $f:D \rightarrow D$ che descrive come l'esecuzione delle istruzioni (archi) trasforma l'informazione osservata  

Dati questi, possiamo formalizzare MOP come

![[Pasted image 20241112094347.png]]
Questo ovviamente combina gli effetti di ogni possibile cammino del CFG che raggiungono v, all fine risulterà non decidibile questa funzione

#### Soluzione calcolata

Come avevamo già descritto la soluzione MFP sarà quello che andremo a calcolare anche se è meno precisa perché aggiunge più rumore

![[Pasted image 20241112100051.png]]
![[Pasted image 20241112102633.png]]

Essendo che MFP prende il merge, quindi raccoglie tutto, non può escludere certi cammini che ad esempio la MOP escluderebbe.

Calcolare sull'intero cammino che fa MOP è più preciso

La differenza sta nella funzione distributiva

#### Funzione distributiva

é una funzione che distribuisce sull'operatore di merge

![[Pasted image 20241112103549.png]]

e se $f$ è distributiva (e tutti i nodi del programma sono raggiungibili)

![[Pasted image 20241112103500.png]]

Esempio graficamente
![[Pasted image 20241112104033.png]]
Questo ci dice che abbiamo un approccio algoritmico per calcolare la MOP

#### Funzione totale distributiva 

![[Pasted image 20241112104604.png]]

Ad esempio sommare (add) non è distributiva

#### Approccio algoritmico

Quindi le analisi si divideranno nelle:
- analisi distribuitive (riguardano problemi semplici) che cerca informazioni che guardano il come avviene il calcolo, quindi più vicino alla sintassi (errore dovuto al CFG)
- analisi non distributive (riguardano problemi difficili) che cerca informazioni sul cosa che viene calcolato, quindi sulla memoria (errore dovuto al calcolo della soluzione per punto fisso)

In base alla direzione dell'analisi
- __Algo Forward__
	![[Pasted image 20241112111657.png]]
- __Algo Backward__
	![[Pasted image 20241112112233.png]]

Se gli algoritmi convergono allora abbiamo soluzione e corrisponde nel framework monotono alla soluzione MFP

#### Soluzione ideale

Sia mop che mfp non sono proprio soluzioni totalmente corrette, perché idealmente si dovrebbe calcolare su tutti i cammini possibili nel senso di eseguibili dalla entry al nodo di interesse


#### :LiExternalLink: REFERENZE: