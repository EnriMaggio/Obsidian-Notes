#### :LiCalendarClock:  08/01/2025 - 15:55

fa parte delle analisi non distributive, ovvero che guardano cosa viene calcolato

---
#### Constant propagation

Dato un programma, vuole determinare il valore costante di ogni variabile nei vari punti di programma, se le variabili non sono costanti (o potenzialmente non costante). l'analisi risponde non so. Questa analisi è una forma di valutazione parziale (propagazione simbolica)

![[Pasted image 20250108160548.png]]

Per esempio

![[Pasted image 20250108161909.png]]


---
#### Dominio astratto constant propagation

ora specifichiamo le proprietà che vogliamo osservare con precisione astraendo gli stati

![[Pasted image 20250108163012.png]]

---
#### Semantica astratta constant propagation

dobbiamo astrarre gli stati 

![[Pasted image 20250108164300.png]]


---
#### Soluzione mop constant propagation

Vogliamo vedere se per la semantica astratta applicata ad ogni stato, mi dice se ogni variabile è costante (che valore) o meno.

La MOP sarà quindi

![[Pasted image 20250108165101.png]]

da notare che la soluzione è collecting perchè dobbiamo raccogliere tutte le informazioni eseguendo il programma mano a mano (forward).

---
#### Trasferimento operazioni

ora dobbiamo trasferire il calcolo delle operazioni concrete nel dominio astratto. Nel concreto abbiamo parti di interi ed eseguiamo operazioni su questi interi. Adesso si devono effettuare le operazioni nel dominio astratto

![[Pasted image 20250108165807.png]]

Con questo possiamo definire la semantica delle operazioni (espressioni)

![[Pasted image 20250108170411.png]]
![[Pasted image 20250108170810.png]]

e la semantica dei comandi

![[Pasted image 20250108184833.png]]


---
#### Non distributività

Questa analisi non è distributiva, il che significa che la soluzione MFP non è uguale alla MOP, ma la approssima.Possiamo arrivare ad una conclusione attraverso un sistema di disequazioni, inoltre la semantica astratta è monotona e il dominio è ACC, quindi MFP esiste ed è calcolabile

![[Pasted image 20250110094632.png]]

come si vede dall'esempio il risultato tra MFP e MOP sono diversi, con la MFP che è più astratta (più grande)


---
#### Esempi

![[Pasted image 20250110101519.png]]

#### :LiExternalLink: REFERENZE: