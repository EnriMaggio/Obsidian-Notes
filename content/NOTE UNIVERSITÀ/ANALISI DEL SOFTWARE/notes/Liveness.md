#### :LiCalendarClock:  29/10/2024 - 09:42

#### Introduzione Liveness

Indica quali sono le variabili che sono le live, nel concreto consiste che il loro valore hanno un uso da qualche parte nel codice, quindi hanno una definizione precedente in qui sono stati inizializzati

Per determinare che una variabile è viva, bisogna guardare ai suoi usi all'indietro fino alla sua definizione, per questo sarà un'analisi di tipo backward sulla sintassi

![[Pasted image 20241126161136.png]]

Bisogna distinguere bene la differenza tra variabili usate e definite

![[Pasted image 20241126154556.png]]

Possiamo dire che x è live se si trova tra un nodo che definisce x e uno che utilizza x

Invece non è live quando si trova tra due definizioni (riassegnata prima del suo utilizzo) o se non viene mai usata (x è dead)

![[Pasted image 20241126155315.png]]

Un altro obiettivo della liveness è quella di identificare variabili non inizializzate

#### Definizione Normale

Una variabile $x$ è live su $v$ se esiste un cammino $\pi$ che 
$$
\pi:v \rightarrow exit
$$ tale che $v$ non contiene definizioni di $x$ ed esiste almeno un uso di $x$ in $\pi$ che non segue un'altra definizione

Quindi esistono $\pi_1, \pi_2, k$ (primi due cammini e l'ultimo arco) in cui $k$ contiene un uso di $x$, $\pi_1$ non contiene definizioni di x

![[Pasted image 20241126162700.png]]

#### Processo analisi

Dobbiamo capire come collezionare l'informazione e come il blocco la modifica

![[Pasted image 20241126162910.png]]

Le situazioni in cui abbiamo che le variabili sono live sono le seguenti

![[Pasted image 20241126163452.png]]

Definiamo quindi due espressioni:

![[Pasted image 20241126172543.png]]

Esempio

![[Pasted image 20241126175339.png]]

#### Approccio semantico

In questo approccio si vanno prima ad individuare:
- **Il Dominio**: $P(Var)$ collezione degli oggetti astratti che osserviamo, in questo caso le variabili live (dominio finito)
- **Funzione di trasferimento**: Abbiamo una analisi backward avendo la seguente semantica astratta
	![[Pasted image 20241127102305.png]]

La soluzione MOP è definita come l'unione dei cammini dei nodi precedenti ed è indicata con $L^*$ 

![[Pasted image 20241127102540.png]]

Per la computazione dobbiamo costruire un sistema di disequazioni la cui soluzione migliore è la soluzione corrispondente al sistema ed è la soluzione che riusciamo a calcolare per ogni punto di programma

Ovviamente la MOP non è decidibile, che lo è se esiste MFP con semantica distributiva


#### True liveness

Il problema che rimane per il modo in cui abbiamo costruito l'analisi è che possono rimanere dei falsi positivi

![[Pasted image 20241127110129.png]]

Esempio

![[Pasted image 20241127112333.png]]

Il concetto di vero uso sta per il fatto che una variabile venga usata nel nodo successivo

 ![[Pasted image 20241127113045.png]]

Nell'approccio algoritmico cambiano le definizione di Tliveout e Tlivein

![[Pasted image 20241127113747.png]]

Mentre nell'approccio semantico cambia alcuni elementi della semantica

![[Pasted image 20241127114614.png]]
#### :LiExternalLink: REFERENZE: