#### :LiCalendarClock:  31/10/2024 - 15:51

L'idea di fondo di data and mutable store è quello di non essere più vincolati ta tipi semplici come bool, int e skip, ma vorremmo estendere il nostro linguaggio con qualsiasi tipo.

Si introduranno quindi delle strutture dati mantenendole nella forma più semplice possibile

Avendo un qualsiasi tipo avremo la necessità quindi di modificare le referenze di memoria, in modo che possano essere dinamiche

#### Prodotto tra tipi

Il tipo prodotto della forma
$$
T_1 * T_2
$$ permette di avere coppie, o meglio tuple, di valori dei tipi $T_1$ e $T_2$ 

#### Sintassi prodotti

Estendiamo il linguaggio

![[Pasted image 20241031160630.png]]

#### Tipaggio prodotti

![[Pasted image 20241031160931.png]]

#### Semantica operazionale Prodotti

Dobbiamo aggiungere ai valori (terminali) la coppia di valori del costrutto prodotto di tipi. A runtime invece la semantica si fa left to right

![[Pasted image 20241031161910.png]]

#### Records sintassi

I records sono delle "collezioni" in cui gli elementi sono composti da una etichetta(label), ovvero una stringa, con associato il corrispettivo costrutto (valore finale o qualsiasi oggetto da valutare)

![[Pasted image 20241031163951.png]]

#### Records Tipaggio

Ogni elemento di un record semplicemente avrà il suo tipo

![[Pasted image 20241031164427.png]]

#### Records Semantica operazionale

![[Pasted image 20241031165408.png]]

#### Mutable store sintassi

L'obbiettivo del mutable store è quello di avere locazioni dinamiche, ovvero variabili che in memoria possono modificare il loro contenuto nel tempo, ora questi contenuti possono essere di qualsiasi tipo, non solo int, bool o unit

![[Pasted image 20241031170440.png]]

#### Mutable store Tipaggio

![[Pasted image 20241031171002.png]]

#### Mutable store Semantica operazionale

Adesso la funzione store cambia, non restituisce più solo interi, ora restituirà valori di qualsiasi tipo (sempre associati a locazioni).

Nulla ci vieta di fare locazioni di locazioni (indirizzi in memoria che puntano ad altri indirizzi)

![[Pasted image 20241031172210.png]]
![[Pasted image 20241031172445.png]]


#### :LiExternalLink: REFERENZE: