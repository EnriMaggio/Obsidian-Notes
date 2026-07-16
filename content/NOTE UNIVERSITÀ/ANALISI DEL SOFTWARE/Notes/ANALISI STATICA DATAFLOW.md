#### :LiCalendarClock:  29/10/2024 - 09:04

Il nostro analizzatore in sostanza deve decidere se per una certa proprietà di un programma, l'analizzatore riesce a dire se vale quella proprietà

![[Pasted image 20241029091321.png]]

#### Idea analisi statica

Sappiamo che la semantica è definita nel seguente modo 
![[Pasted image 20241029092510.png]]
- $P(D)$ è l'insieme che rappresenta tutte le semantiche del nostro programma
- $Q \subseteq P(D)$ è il dominio che rappresenta tutte le semantiche del nostro programma
- che soddisfano la proprietà invariante  

#### Analisi statiche (no semantica)
- Control flow analysis
- Data Flow analysis: come l'informazione fluisce dentro il programma (durante l'esecuzione)

Nella data flow analysis si riesce ad approssimare nella sintassi, questo perchè l'analisi non conta gli stati del programma ma andrà a guardare la relazione sintattica tra gli elementi del programma

I tipi di analisi distributive del Data Flow Analysis che approssimano bene sulla sintassi sono
- [[Available Expression]]
- [[Liveness]]
- [[Copy propagation]]
- [[Reaching definition]]
#### CFG based

Questi tipi di analisi sono cfg based, quindi che seguono un algoritmo ricorsivo di calcolo della proprietà desiderata sul cfg

La costruzione dell'analisi è composta da
- costruire il cfg
- analisi del codice Intra procedurale (sul cfg singolo)

Quello che andremo a vedere è capire come l'informazione di interesse viene trasformata dentro un blocco

![[Pasted image 20241029100337.png]]

#### Formal framework

Grazie a questo strumento risuciamo a formalizzare l'analisi statica attraverso la semantica, che in questo caso riesce a guardare dentro la memoria

E un contesto di costruzione dell'analisi basato sul calcolo semantico. Ci dice come altera le info man mano che si raccolgono

Ci sono due ingredienti nel Formal framework:
- $D$ formalizziamo l'informazione astratta che vogliamo analizzare
- $F$ costruire la semantica induttivamente sulla sintassi che trasforma l'informazione osservata (abstract edge effect)

Dal programma costruiremo un sistema di disequazioni (una per ogni punto di programma) in $N$ incognite cercando la migliore soluzione possibile.

Da questo raggiungiamo il nostro obiettivo cioè la soluzione del sistema che in generale approssima la soluzione ==**MOP**== (Merge over all path), ovvero combinare tutte le possibili soluzioni su tutti i possibili cammini

In pratica possiamo calcolare l' ==**MFP**== (Soluzione del sistema) che approssima MOP e se coincidono abbiamo ridotto al minimo l'errore

#### Formal framework su Available Expression

Dobbiamo caratterizzare l'insieme di tutte le espressioni che sono disponibili in un punto di programma all'interno di una variabile
- Insieme $Ass$ $x \leftarrow e$  $x \notin Var(e)$ 
- Dominio astratto $P(Ass), A \subseteq Ass$  

Poi dobbiamo caratterizzare la funzione di trasferimento, ovvero come l'informazione viene trasformata. E una semantica astratta definito in modo induttivo sul linguaggio del CFG

![[Pasted image 20241030090718.png]]

#### La soluzione

Una espressione è definitivamente disponibile in $v$ se è disponibile in ogni cammino che va dall'entry point del CFG a $v$

![[Pasted image 20241030092008.png]]

#### Perdita di precisione

Con questo si perde precisione perchè appunto prendiamo tutti i cammini del CFG che contengono i cammini eseguibili in comune (sottoinsieme dei cammini del CFG). Ad esempio

![[Pasted image 20241105114234.png]]

Inoltre non si guarda il valore delle variabili 

![[Pasted image 20241105114511.png]]
#### Caratteristiche dell'analisi

In questa analisi vogliamo che

- __Termini__
	viene garantita dalla monotonia del trasformatore semantico che calcola su domini finiti (ACC ovvero ascending chain condition che sono domini infiniti ma con catene ascendenti non infinite)
	
	![[Pasted image 20241105115014.png]]
- __Sia corretta__
	ovvero che contiene l'informazione precisa e che viene garantita per costruzione (fix point). Si basa sul legame sintassi e semantica
- __Precisa__
	si cerca come obiettivo l'ottimalità, si abbassa la precisione perchè si considerano cammini non possibili ma che sono necessariamente considerati
	
	![[Pasted image 20241105115447.png]]

#### Costruzione dell'analisi

Come già descritto, costuiremo la mop attraverso il CFG creando un sistema di disequazioni avendo una disequazione per ogni arco più una iniziale.

Le incognite presenti nel sistema di disequazioni sono esattamente il risultato dell'analisi per ogni punto di programma 

![[Pasted image 20241105121643.png]]

esempio dato il seguente CFG a sinistra, inizializziamo le disequazioni

![[Pasted image 20241105122153.png]]

Ora calcoliamo le disequazioni con cinque incognite

![[Pasted image 20241112091339.png]]

Si può effettuare lo stesso calcolo con round robin che calcola in base alla colonna corrente e non guardando i valori nella colonna precedente

![[Pasted image 20241112091156.png]]
#### :LiExternalLink: REFERENZE: