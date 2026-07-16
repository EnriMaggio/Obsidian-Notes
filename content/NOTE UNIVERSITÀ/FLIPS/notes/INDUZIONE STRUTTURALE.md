#### :LiCalendarClock:  15/10/2024 - 19:31

\#IamGonnaDeleteArc01
E una specie di generalizzazione dell'induzione matematica, viene utilizzata per dimostrare che una certa proposizione P(x) vale per tutti gli x che è un certo tipo di struttura definita ricorsivamente, come formule, liste o alberi (in genere grammatiche). Ci da la possibilità di ragionare e dimostrare proprietà su programmi, perchè questi contengono strutture con sottostrutture (while, if, ecc. ecc.) e quindi riusciamo a esprimere oggetti più grossi in oggetti più piccoli

L'idea è quella di dimostrare il sotto-elemento/elemento più piccolo, così la struttura più grande che contiene questi sotto-elementi sono automaticamente verificati

dimostra proprietà di insiemi finiti sintattici, usando una prova che segue dalla struttura della grammatica che definisce l'insieme stesso. Anche qua rispettando 2 condizioni:
1. **CASO BASE:**  dimostrare che P(x) vale per tutti i casi base x
2. **CASO INDUTTIVO:** dimostrare che se P(l) (per l intendiamo un non terminale della grammatica) e M può essere ottenuto da l applicando una regola ricorsiva, allora P(M) è vera. Se la grammatica prevede più produzioni bisogna dimostrare più casi induttivi
#### NUMERI NATURALI SU INDUZIONE STRUTTURALE:
I numeri naturali li possiamo esprimerli con una grammatica

![[Pasted image 20241015220813.png]]
(dove zero e succ sono due token)

Se volessi scrivere 3 allora dovrei fare succ(succ(succ(0))), in pratica una enumerazione unaria. Abbiamo quindi dato un'altra definizione sintattica ai numeri naturali e come prima possiamo applicarli degli f per provare certe proprietà

![[Pasted image 20241015222836.png]]
![[Pasted image 20241015223100.png]]
#### INDUZIONE STRUTTURALE SU ALBERI BINARI:
gli alberi binari non sono altro nodi che hanno due rami che vanno in figli che sono a loro volta o dei nodi oppure delle foglie 
![[Pasted image 20241015223436.png]]
Induttivamente è definita in questo modo
![[Pasted image 20241015223519.png]]
La sintassi (grammatica) è questa

![[Pasted image 20241015223840.png]]
avendo una grammatica l'albero è definito come un programma (espresso in sottoprogrammi).
E anche qua io posso applicare induttivamente delle f a questi alberi

![[Pasted image 20241015224849.png]]
ecco due esempi
![[Pasted image 20241015225451.png]]

Per provare una proprietà sugli alberi si fa con l'induzione

![[Pasted image 20241015230008.png]]

eccone un esempio

![[Pasted image 20241016095257.png]]

#### INDUZIONE STRUTTURALE SU ESPRESSIONI ARITMETICHE:
La grammatica è la seguente

![[Pasted image 20241016095905.png]]

L'astrazione sintattica di questo oggetto è rappresentato anche esso dagli alberi binari con l'unica differenza che i nodi sono etichettati

![[Pasted image 20241016100122.png]]
![[Pasted image 20241016100538.png]]

E anche in questo caso possiamo applicare delle funzioni a queste espressioni

![[Pasted image 20241016100658.png]]


#### :LiExternalLink: REFERENZE: