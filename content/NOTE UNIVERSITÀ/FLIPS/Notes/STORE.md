#### Data: 09/10/2024 - 10:30
#### Linked Notes: 

Per fare questa funzione store abbiamo prima bisogno delle ==**funzioni parziali**==, quindi cosa sono?
$$
f:A\rightharpoonup B
$$
Avendo due insiemi ($A,B$), sono delle funzioni che ritornano un elemento di $B$ per alcuni elementi di $A$, cioè nel dominio di $A$ non si andranno a considerare tutti i suoi elementi. Potrebbe essere che $f(a)$ non sia definita per alcuni $a$ in $A$, oppure che f non è definita per nessun elemento di $A$
![[Pasted image 20241009104304.png]]
Dopo questa piccola regressione possiamo parlare dello Store che è il modo più semplice per implementare questa sorta di ==**mapping**== tra le nostre locazioni con i numeri interi e prenderà la seguente forma:
$$
s:\mathbb{L} \rightharpoonup \mathbb{Z}
$$
avremo quindi un insieme quindi di funzioni parziali finite nel seguente come ad esempio
$$
\{ l_1 \rightarrow 3,l_2 \rightarrow 6, l_3 \rightarrow 7\}
$$
Avendo questo possiamo fare un ==**aggiornamento**== nel seguente modo
![[Pasted image 20241009105116.png]]La store determina il comportamento del nostro programma, cioè in esecuzione il programma si comporta in modo dipendenti dai cambi di stati di memoria