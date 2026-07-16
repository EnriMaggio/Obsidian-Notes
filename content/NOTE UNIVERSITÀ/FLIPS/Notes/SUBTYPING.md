#### :LiCalendarClock:  12/11/2024 - 15:51

Il subtyping è molto utile perchè permette di fare riutilizzo del codice, quindi risparmia tempo al programmatore

Fa parte del [polimorfismo](https://it.wikipedia.org/wiki/Polimorfismo_(informatica) con il subtype polymorphism nei linguaggi orientati ad oggetti (per l'estensione di classi)

#### Motivazione

é per non avere a runtime un deadlock a causa di tipi non permissivi o rilassati. L'obbiettivo è quindi tipare più programmi che a buon senso vanno in esecuzione senza problemi di runtime

![[Pasted image 20241112164900.png]]

#### Subsumption

ora vedremo piano piano che c'è una relazione tra tipi ovvero
$$
T<:T'
$$
Ovvero che il tipo $T$ è un sottotipo $T'$, bisogna tenere a mente che il sottotipo non ha meno cose del tipo a cui è soggetto, è più piccolo da un punto di vista concettuale (più contestuale), invece è come se estendesse $T'$ aggiungendo informazioni

![[Pasted image 20241112165851.png]]
![[Pasted image 20241112170541.png]]

Andremo a _"tagliare"_ una parte del tipo $T$ 

#### Regole inferenza

![[Pasted image 20241112171129.png]]

#### Subtyping su record

![[Pasted image 20241112172139.png]]

#### Subtyping su Funzioni

![[Pasted image 20241112174426.png]]

Ad esempio sia una funzione
$$
f:T_1 \rightarrow T_2
$$
l'idea sta che in molti altri contesti possiamo utilizzare $f$ ma non necessariamente con lo stesso tipo, in modo che possiamo passare più informazioni a seconda del contesto in qui viene applicato

![[Pasted image 20241113112403.png]]

ecco un esempio dove non funziona

![[Pasted image 20241113114214.png]]

#### Subtyping sui prodotti e somme
![[Pasted image 20241113114412.png]]

#### Subtyping Down-Casts

![[Pasted image 20241113115129.png]]

#### :LiExternalLink: REFERENZE: