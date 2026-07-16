#### :LiCalendarClock:  20/10/2024 - 12:03

#### Cosa è?
Come dice il nome il CFG è un grafo diretto che viene generato dalla sintassi del programma che stiamo analizzando. Il CFG descrive il flusso dell'esecuzione di un programma direttamente dalla sintassi

Questo CFG ci permette di separare l'aspetto di controllo dall'aspetto di manipolazione degli stati della macchina
#### Come è fatto?
Questo grafo è composto da una coppia del tipo 
$$
G=(N,E)
$$
- N sono i nodi che rappresenteranno lo stato/memoria (BASIC BLOCK)
- E sono gli archi che indicano il potenziale di passaggio di controllo. Un arco $e \in E \subseteq NxN$ con $e=(n_i,n_j)$ una coppia di nodi, descrive un possibile passaggio di controllo potenziale da $n_i$ a $n_j$ (possibile perchè in caso di if si possono prendere due strade diverse)

Dato un cfg ci sono degli insiemi:

![[Pasted image 20241020125151.png]]
#### Basic block
sono una sequenza consecutiva massimale di istruzioni con singola entrata e singola uscita (senza branch o più padri). Per semplicità si suppone che esistono un nodo unico $n_0$ che indica il punto di ingresso del programma e un nodo unico $n_f$ che indica il punto di fine del programma

#### Costruzione basic block
Bisogna prendere in input una sequenza di istruzioni e poi per identificare i basic block dobbiamo:
1. Determinare tutti i LEADERS, ovvero la prima istruzione di un basic block che possono essere:
	- prima istruzione di un programma
	- ogni istruzione S che è target da un branch 
	- ogni istruzione successiva a un branch
2. Basic block è costituito da leader più sequenza di istruzioni fino al leader successivo (esclusivo)
 
 ecco un esempio di individuazione dei leaders e dei basic blocks (rosso e verde) e gli archi(frecce) che descrivono il passaggio di controllo
 
![[Pasted image 20241020124620.png]]

#### Linguaggio CFG
Dobbiamo formalizzare le etichette degli archi, questo ci consentirà di attuare modifiche sullo stato che saranno corrispondenti all'istruzione eseguita, per farlo utilizzeremo un linguaggio che sarà il seguente:
![[Pasted image 20241021141230.png]]

Un esempio di CFG è:
![[Pasted image 20241021141343.png]]

La computazione in CFG è la semantica di un cammino nel CFG che parte dal nodo iniziale e arriva a un nodo finale: è una sequenza di archi. La semantica quindi descrive l'effetto dell'arco sullo stato.

L'arco innanzitutto è definito come una tripla
![[Pasted image 20241021142044.png]]

e qua la semantica delle etichette
![[Pasted image 20241021142716.png]]
#### :LiExternalLink: REFERENZE: