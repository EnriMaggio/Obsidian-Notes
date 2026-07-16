#### :LiCalendarClock:  29/10/2024 - 09:38

#### Available expression

l'analisi di available expression va a guardare se ci sono espressioni disponibili, ovvero già calcolate e sostituirle invece di ricalcolare se si incontra in altri punti del programma le stesse espressioni

L'obbiettivo è quello di identificare espressioni che vengono ricalcolate. Queste espressioni si trovano più facilmente nel codice intermedio nel processo di compilazione di un programma, in quanto deve ottimizzare alcune cose tra cui le espressioni

Il risultato di questa analisi è un codice che può essere più snello e veloce

esempi
![[Pasted image 20241029102545.png]]
![[Pasted image 20241029102817.png]]

Generalmente le espressioni disponibili hanno queste caratteristiche
- ovviamente devono essere già calcolate minimo una volta
- l'espressione è disponibile una volta calcolato
- distruggo la espressione quando essa cambia (poi la rigenero)

Due domande da porsi mentre si analizza sulle espressioni sono
- Se è vero che una espressione è valutata sempre prima di un altra espressione
- Una variabile in un punto di programma ha sempre lo stesso valore che avere prima di un altro punto di programma?
#### Semantica operazionale

Per costruire nel concreto questa analisi abbiamo bisogno di una semantica operazionale e di un metodo per dare risposte a queste domande.

Queste risposte però non dovranno darci mai dei falsi positivi mentre sono accettate dei falsi negativi
#### Definizione 
Un'espressione $e$ è disponibile in una variabile $x$ al punto $v$ ($x$ contenitore del valore e $v$ punto di programma in cui ci serve il valore) se
- $e$ deve essere stata valutata in un punto precedente a $v$ e salvata in $x$
- sia $x$ che tutte le variabili in $e$ non devono essere modificate tra la valutazione di $e$ in $x$

![[Pasted image 20241029105556.png]]

L'espressione così non basta per fare la analisi, abbiamo bisogno di sapere ad ogni blocco quali sono le espressioni in entrata e quelle in uscita, o meglio, dobbiamo costruire l'informazione disponibile in output(Avail out) in funzione di quella disponibile in Input(Avail in)

![[Pasted image 20241029111117.png]]

- AVAIL IN (b)
	Sono tutte le espressioni disponibili, intersecate tra di loro, in ingresso di $b$ (blocco)
	![[Pasted image 20241029112515.png]]
- AVAIL OUT (b)
	Sono tutte le espressioni in entrata che non sono state eliminate(kill) unito alle nuove espressioni che  il blocco ha generato (gen)
	![[Pasted image 20241029112559.png]]
	Kill descrive gli assegnamenti che non possono essere disponibili dopo l'esecuzione di $b$ 
	![[Pasted image 20241029113103.png]]
	Gen descrive gli assegnamenti nuovi resi disponibili dopo l'esecuzione di $b$
	
	![[Pasted image 20241029113211.png]]

Notiamo che queste due funzioni sono definite ricorsivamente l'uno con l'altro, quindi se mettiamo in ordine i vari pezzi otteniamo

![[Pasted image 20241029113348.png]]

#### Algoritmo analisi

![[Pasted image 20241029153457.png]]
![[Pasted image 20241029153626.png]]
#### Esempio

La procedura da seguire è:
1. trovare Ass
2. eliminare in Ass quelli non disponibili
3. costruire CFG
4. Gen e Kill di ogni blocco
5. Avail IN (rappresentato con una tabella)

![[Pasted image 20241029155927.png]]

#### Tipologia di analisi

Nell'analisi si può scegliere anche la direzione con cui eseguire la nostra data flow analysis
- Forward(FW)
	dritto, ovvero partendo dal nodo iniziale $n_0$ ho l'informazione iniziale che ogni blocco in input combina l'output dei predecessori
- Backward(BW)
	al contrario, dallo stato finale $n_f$ ho l'informazione finale ("iniziale") dell'analisi che ogni blocco in output combina l'input dei successori
#### :LiExternalLink: REFERENZE: