#### :LiCalendarClock:  13/10/2024 - 15:39

Questo linguaggio avrà una sintassi che comprenderà i seguenti elementi:

![[Pasted image 20241013154237.png]]

La semantica di questo linguaggio caratterizza mediante una funzione matematica gli effetti sullo stato della macchina dell'esecuzione del programma.

Abbiamo bisogno di un'informazione molto importante che è la ==**memoria**==. Per questo si utilizzerà lo stato che descrive la memoria ad ogni passo di esecuzione e la sua semantica è una funzione tra stati, in modo composizionale, ovvero (che la semantica di un costrutto più complesso o grande è composto dalle semantiche dei sotto costrutti che la compongono)
$$
\mathbb{M} = Var \rightarrow Val 
$$
Quindi un $m \in\mathbb{M}$ è una "mappatura" tra una variabile e un valore. Questa semantica ci dice che farà una trasformazione di memorie

in questo caso funziona come un'interprete perchè prende passo passo un'istruzione e dei input e vede la usa esecuzione.

La semantica di un qualsiasi cosa viene indicata con doppie parentesi quadrate

#### Semantica espressioni
La semantica di un'espressione è una funzione che prende in memoria una locazione e associa un valore int o bool (elaborazione/valutare espressione)

![[Pasted image 20241013155529.png]]
#### Semantica dei comandi
La semantica dei comandi è una funzione che fa trasformazioni di insiemi di memoria
![[Pasted image 20241017145916.png]]
![[Pasted image 20241013155712.png]]

#### SEMANTICA OPERAZIONALE SMALL STEP
Insieme di tutte le sequenze di transizioni di stati a partire da quelli iniziali, descritto con un sistema transizionale. In pratica descriveremo tutte le tracce che sono composte da
- stato iniziale
- stato intermedio
- stato di terminazione

![[Pasted image 20241017152638.png]]
Questa semantica operazionale alla fine viene costruita una semantica a punto fisso attraverso un operatore iterabile, monotono totale che è un trasformatore di stati. Ci è utile perchè è un operatore che si applica iterabilmente, quindi può automatizzare la nostra analisi in modo costruttivo passo dopo passo, inoltre ci fa fare induzione sulle tracce

#### SEMANTICA PUNTO FISSO
E definita come coppia
$$
<D,F>
$$ dove
- $D$ è un dominio 
- $F$ è un'operatore semantico, è una funzione totale, [[monotona]] e iterabile

è monotona perchè preserva l'ordinamento degli elementi ed è iterabile perchè posso applicare una funzione n volte ($F:D \rightarrow D$)

Per definire la semantica vera e propria dobbiamo definire un sistema di transizione
$$
<\Sigma, \tau>
$$ dove
- $\Sigma$ è un insieme di stati/configurazioni (fotografia della memoria)
- $\tau$ è una relazione di transizione tra due stati $\tau \subseteq \Sigma x \Sigma$ 

Una transizione è quindi definita come
$$
\sigma_1 \rightarrow \sigma_2
$$
Uno stato terminale invece è definito come
$$
\sigma \text{ è terminale se }
\forall \sigma' \text{ } \sigma\not\rightarrow \sigma'
$$
Questo operatore riesce a ricorstruirmi le tracce

![[Pasted image 20241017161338.png]]
