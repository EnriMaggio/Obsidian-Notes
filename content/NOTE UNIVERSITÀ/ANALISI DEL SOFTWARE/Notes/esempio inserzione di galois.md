#### :LiCalendarClock:  10/12/2024 - 16:56

![[Pasted image 20241210165807.png]]

come funzione di astrazione prendiamo un insieme nel dominio concreto e lo associamo all'insieme più grande nel dominio astratto a cui è minore a tutti gli elementi di quell' insieme

![[Pasted image 20241210170118.png]]
![[Pasted image 20241210170357.png]]
![[Pasted image 20241210170615.png]]

Si può notare che solo tre elementi sono immagini di $\alpha$, gli altri si possono considerarli come _"inutili"_ 

![[Pasted image 20241210170828.png]]

Si può verificare questa cosa con la funzione di $\gamma$ che preso un elemento astratto mi restituisce l'elemento concreto

![[Pasted image 20241210171221.png]]

quindi {2}, {2,4}, {2,6}, {2,4,6} hanno lo stesso significato secondo $\gamma$ quindi ci interessa l'elemento più piccolo più preciso per rappresentare quel significato che incorpora tutti gli altri e in questo caso è {2,4,6}

![[Pasted image 20241210171626.png]]
![[Pasted image 20241210171812.png]]

si può vedere come la monotonia venga rispettata 

![[Pasted image 20241210172454.png]]
![[Pasted image 20241210172522.png]]

gli elementi inutili li andiamo a togliere con inserzione di galois

![[Pasted image 20241210172951.png]]
![[Pasted image 20241210173336.png]]
![[Pasted image 20241210173521.png]]

vengono accorpati gli elementi astratti che hanno lo stesso significato astratto, di fatto riduciamo il dominio astratto eliminando elementi che hanno significato equivalenti ad un altro elemento più concreto
#### :LiExternalLink: REFERENZE: