#### :LiCalendarClock:  11/01/2025 - 15:32

Analizzare gli intervalli porta ad esaminare un dominio infinito e non acc (catene ascendenti infinite)

![[Pasted image 20250111154850.png]]

Qualsiasi elemento x all'interno ha una quantità infinita di altri elementi(intervalli) che sono più grandi di x, siccome con il punto fisso collezioneremo oggetti, il punto fisso può divergere appunto perché le catene sono ascendenti e infinite

---
#### Analisi intervalli

Piuttosto che ai valori costanti delle variabili, saremmo più interessati a determinare il range dei valori che può assumere una variabile in un certo punto di programma durante l'esecuzione. L'approssimazione sui intervalli riguarda il fatto che verranno riempiti dei buchi nell'intervallo dei valori che una variabile può acquisire nel concreto, questo li porta a essere convessi

![[Pasted image 20250111155526.png]]

quindi se x ha un range di valori nel concreto di (1,5,20,35), l'intervallo astratto considera anche i buchi, perdendo precisione aggiungendo rumore tra il valore minimo e massimo della variabile.

---
#### Dominio astratto intervalli

il dominio degli elementi che vogliamo osservare con precisione è l'insieme di tutte le coppie tale che il valore minimo della coppia è un intero unito con $- \infty$ e il valore più grande è un intero con $\infty$

![[Pasted image 20250111160110.png]]

Nel concreto invece abbiamo insiemi di valori sull'insieme degli interi per le variabili parti di z


---
#### Connessione di galois per gli intervalli

dobbiamo avere una connessione di GI per andare e tornare dal mondo astratto al concreto

![[Pasted image 20250111161203.png]]

Quindi esiste la miglior approssimazione per un insieme, in questo il più piccolo intervallo che contiene l'insieme da cui partiamo

- __Alpha $\alpha$__
	![[Pasted image 20250111160839.png]]
	Con min e max:
	![[Pasted image 20250111160913.png]]
- __Gamma $\gamma$__
	![[Pasted image 20250111161032.png]]


---
#### Operazioni del reticolo (dominio astratto)

due intervalli sono in relazione tra di loro quando un intervallo è contenuto dentro l'altro, ovvero quando gli elementi dell'intervallo contenuto sono anche elementi di quello che lo contiene

![[Pasted image 20250111164553.png]]

Il LUB è l'intervallo più piccolo che contiene gli intervalli che stiamo combinando/relazionando, ovviamente sarà un intervallo più grande e più generico (unendo tra i due intervalli il lower bound più piccolo e l'upper bound più grande)

![[Pasted image 20250111165016.png]]

Il GLB è l'intervallo più grande contenuto in entrambi (quasi come l'intersezione) prendendo il massimo tra i lower bound e il minimo degli upper bound tra i due intervalli

 ![[Pasted image 20250111165541.png]]


---
#### Trasferimento delle operazioni sul dominio astratto

operazioni tra i valori

- __Somma__
	![[Pasted image 20250111170004.png]]
- __Negazione__
	significa negare gli estremi, ovvero invertirli (per mantenere il fatto che è un intervallo)
	![[Pasted image 20250111170133.png]]
- __Confronto__
	![[Pasted image 20250111171828.png]]
	![[Pasted image 20250111171909.png]]


---
#### Dominio concreto sugli stati

![[Pasted image 20250111172821.png]]

---
#### Soluzione cercata

l'ideale è la soluzione mop

![[Pasted image 20250111173758.png]]


---
#### Semantica degli intervalli 

abstract edge effect (semantica astratta sul CFG)
![[Pasted image 20250111174947.png]]

Questa semantica non è distributiva, quindi non possiamo calcolare la MOP come soluzione MFP (sistema di disequazioni)

---
#### Soluzione MFP

è di tipo forward e possible (sovrastimiamo)

![[Pasted image 20250111175345.png]]

esempio

![[Pasted image 20250113164133.png]]

---
#### Accelerazione dell'analisi

l'analisi di per sè funziona, ma risulta evidente che quando sono presenti tantissime iterazioni risulta estremamente inefficiente, per questo si cerca di velocizzare il processo utilizzando Widening e Narrowing anche se si va a perdere più precisione

- __Widening__
	Accelera computazioni di punto fisso garantendo la convergenza
	 ![[Pasted image 20250113165905.png]]
	
- __Narrowing__
	text
#### :LiExternalLink: REFERENZE: