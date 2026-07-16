#### :LiCalendarClock:  09/12/2024 - 09:05

#### Strumenti fondamentali

come descritto In [[INTERPRETAZIONE ASTRATTA]] il legame tra il mondo concreto (nel quale vogliamo calcolare le varie risposte) e il mondo astratto (nel quale possiamo dare delle risposte) avviene per ==connessione di galois== e utilizzando il processo di astrazione e concretizzazione. E estremamente necessario che il legame sia bilaterale, ovvero poter andare nel mondo astratto e ritornare nel mondo concreto

---
#### Connessione di Galois

è una coppia di funzioni $\alpha,\gamma$ monotone definite tra un dominio concreto $C$ e un dominio astratto $A$, quest'ultimi due sono reticoli completi

- **funzione di astrazione $\alpha$**
	![[Pasted image 20241209093515.png]]
- **funzione di concretizzazione $\gamma$**
	![[Pasted image 20241209093724.png]]

graficamente, un elemento $c$ che si trova nel dominio di $C$ con una sua controparte nel dominio astratto $\alpha(c)$ (attraverso $\alpha$) e quest'ultimo è minore di un valore $a$ che si trova nel dominio $A$, allora la concretizzazione con $\gamma(a)$, che lo porta nel mondo concreto, sarà maggiore di $c$ 

![[Pasted image 20241209094610.png]]

La notazione è la seguente

![[Pasted image 20241209095157.png]]


---
#### Inserzione di Galois

Un'inserzione di Galois è più raffinato rispetto alla connessione, perchè non avrà nel dominio astratto elementi inutili, cioè che ogni elemento astratto ha un proprio significato concreto specifico (non hanno lo stesso $\gamma$) 

![[Pasted image 20241209101153.png]]

La migliore approssimazione in generale è equivalente a dire che 

![[Pasted image 20241209095616.png]]

ovvero nel primo caso se si astrae e dopo si concretizza si perde informazioni su $c$, e il secondo ci dice che ci sono elementi nel dominio astratto che sono inutili rispetto ad altri, e verrano diciamo _"inclusi"_ (che sono elementi più grandi) con gli elementi cha hanno significato (più piccoli) in base alla proprietà che stiamo osservando 

Questo concetto è importante perchè ==_ogni connessione di galois può essere ridotta ad una inserzione di galois_==, rendendo il dominio astratto più snello, eliminando elementi inutili per cui il loro significato è lo stesso ad un elemento più preciso

[[esempio inserzione di galois]]


---
#### Formalismi equivalenti 

Sono formalismi che che non hanno bisogno di astrazione, ma solo di lavorare sul dominio concreto (scelgo gli elementi da osservare approssimamente)


---
#### Operatore di chiusura superiore (UCO)

è una tipologia di funzioni che si può definire su un qualunque dominio, purché sia ordinato. L'uco associa ad ogni elemento concreto la sua migliore approssimazione, quindi gli elementi più vicini con più precisione


è definita come.

![[Pasted image 20241210180024.png]]
![[Pasted image 20241210180358.png]]

[[esempio grafico uco]]

---
#### Moore Family

è un particolare tipo di sottodominio

![[Pasted image 20241210182916.png]]

esempio di non moore family
![[Pasted image 20241210183152.png]]

Di fatto l'insieme dei punti fisso di un uco $p:p\rightarrow p$ formano una moore family di $p$ 

---
####  Conclusione

Infine sono tutti i metodi di rappresentare un dominio astratto che coesistono e sono equivalenti

![[Pasted image 20241210183757.png]]
![[Pasted image 20241210184125.png]]


---
#### Modelli a confronto

moore : descrive domini astratti, il sottoreticolo con gli elementi che scelgo di osservare con precisione

uco : come associo ad ogni elemento concreto la proprietà che ho deciso di osservare con precisione

IG: che relazione c'è tra gli oggetti concreti e una rappresentazione di ciò che voglio osservare con precisione

- **GI vs MOORE FAMILY**
	![[Pasted image 20241211092751.png]]
- **UCO vs GI**
	![[Pasted image 20241211093927.png]]
- **GI vs UCO**
	![[Pasted image 20241211094132.png]]
- **UCO vs MOORE FAMILY**
	![[Pasted image 20241211094357.png]]
- **MOORE FAMILY vs UCO**
	![[Pasted image 20241211094450.png]]


---
#### Mettere insieme domini astratti 

Nello stesso dominio concreto possiamo osservare più proprietà diverse, di fatto abbiamo un numero possibili di astrazioni sul dominio concreto. Tutto ciò è possibile con il reticolo delle interpretazioni astratti

![[Pasted image 20241216091823.png]]

avendo queste condizioni, se realizzo questa struttura, allora l'insieme di tutte le sue astrazioni che si possono fare è un reticolo completo 

![[Pasted image 20241216092533.png]]
#### :LiExternalLink: REFERENZE: