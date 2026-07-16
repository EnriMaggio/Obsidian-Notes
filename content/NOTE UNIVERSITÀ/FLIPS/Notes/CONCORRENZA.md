#### :LiCalendarClock:  20/11/2024 - 15:33

#### Introduzione

Adesso si vedrà un nuovo tipo di paradigma di programmazione, ovvero quello concorrente, consiste in generale di più thread che eseguono non più in modo sequenziale ma in modo concorrente. Sono in competizione tra di loro maggiormente per le risorse. Da non confondere che non sempre vanno in parallelo i thread 

La concorrenza è utile e anche interessante perchè l'HW per come è stato costruito è intrinsicamente parallelo

![[Pasted image 20241120155534.png]]

#### Sfide

I thread hanno in generale molti stati, man mano che i thread aumentano il numero di stati aumenta esponenzialmente ed è importante per la verifica: gli stati raggiungibili devono essere Sound(corretti)

Inoltre i thread condividono o utilizzano le stesse risorse, c'è bisogno di una gestione di mutua esclusione per non avere dati inconsistenti o non integri, o peggio, andare in deadlock. Bisogna evitare le data race, succede quando i dati fanno una corsa libera senza sincronizzazione tra i vari thread

![[Pasted image 20241120161216.png]]
![[Pasted image 20241120161658.png]]

#### Linguaggio concorrente

estendiamo il linguaggio

![[Pasted image 20241120162645.png]]
![[Pasted image 20241120162856.png]]
![[Pasted image 20241120173655.png]]

#### Race conditions

Non è più sound quando c'è race condition

![[Pasted image 20241120174628.png]]

Per evitare ciò si deve implementare un meccanismo di mutua esclusione sull'area di memoria condivisa

#### Costrutti Lock e Unlock

sono simili ai semafori.

Ora nella configurazione si aggiunge un nuovo campo $\mu$ che \ica lo stato di mutex associato ai valori booleani

![[Pasted image 20241120175451.png]]

Esempio

![[Pasted image 20241120175834.png]]

Esempio di deadlock

![[Pasted image 20241120180142.png]]

#### Trace equivalence sui programmi concorrenti

Cambiano rispetto ai programmi sequenziali, questo perchè i thread possono non finire esattamente con un valore finale (possono andare a runtime forever). A questo punto si guardono le tracce parziali

Ora per qualsiasi traccia di un programma $e_1$ ci sarà $e_2$ che avrà un solo trace che con una serie di passi cerca di allinearsi con $e_1$ 

![[Pasted image 20241120181744.png]]

#### Esempi

![[Pasted image 20241121091355.png]]
![[Pasted image 20241121091449.png]]

#### Quindi

La trace equivalence non è preservata dai contesti paralleli
![[Pasted image 20241121091729.png]]

Hanno più capacità osservazionale. Si può aggiustare la trace equivalence aggiungendo una terza regola, se sono trace equivalent due programmi lo devono essere anche in un qualsiasi programma parallelo, ovvero che sia una congruenza

![[Pasted image 20241121092831.png]]

#### Bisimilarità

Prima abbiamo bisogno di parlare di **similarità**, ovvero quando un programma simula un altro facendo un numero di passi per allinearsi con lo stato che è stato raggiunto prima dal programma simulato in un solo passo

![[Pasted image 20241127163747.png]]
![[Pasted image 20241127163821.png]]

se due programmi si simulano l'uno con l'altro, non implica che i due programmi siano **bisimili** perchè non si sa chi inizia a fare la _mossa_ e in seguito non si sa quanti passi fanno entrambi le parti per allinearsi con lo store

![[Pasted image 20241127164240.png]]

![[Pasted image 20241127164256.png]]

Per definizione la simulazione e la bisimulazione sono preservati da contesti paralleli

![[Pasted image 20241127165234.png]]

#### Costrutto per gestire regioni critiche

E un costrutto per evitare race condition, quindi garantisce la mutua esclusività sulle risorse

![[Pasted image 20241127170636.png]]
![[Pasted image 20241127171529.png]]
![[Pasted image 20241127173948.png]]

#### Non determinismo

Il non determinismo è utile per rappresentare situazioni di evoluzioni di un programma in cui non ho tutte le informazioni per decidere in modo deterministico

![[Pasted image 20241127175746.png]]


---
#### Comportamenti persistenti

Lo possiamo fare attraverso il punto fisso

![[Pasted image 20241211161505.png]]
![[Pasted image 20241211162808.png]]

---
#### Data race e regioni critiche

![[Pasted image 20241211162939.png]]
![[Pasted image 20241211163016.png]]
#### :LiExternalLink: REFERENZE: