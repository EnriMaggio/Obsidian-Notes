-=#### :LiCalendarClock:  29/10/2024 - 09:41


### Cosa è

La copy propagation controlla se ci sono copie di variabili, ovvero quando una coppia di variabili hanno lo stesso valore. Si cerca di riutilizzare le variabili il più possibile

![[Pasted image 20241202092525.png]]

Come si vede nell'esempio la copy propagation è propedeutica per per la  liveness, così da ottimizzare il codice

La propagazione di una variabile x è data dalla analisi che mantiene ad ogni punto di programma, l'insieme di tutte le variabili che sicuramente contengono una copia di x.

Ogni occorrenza di una copia x può essere sostituita con x

Ovviamente cerchiamo una generalizzazione in cui andiamo a propagare tutte le copie di varie variabili in ogni punto di programma

L'informazione osservata è una coppia osservata
$$
\text{Var x Var}
$$
Un esempio è 
$$
(x,y) \rightarrow \text{x è copia di y}
$$ --- 
#### Approccio Algoritmico

L'analisi è di tipo:
- **FORWARD** perchè andremo a vedere per primo le variabili inizializzata, per poi andare avanti nel futuro a vedere se ci saranno copie
- **DEFINITE** tutti i cammini che portano al punto devono avere l'informazione di essere copia

![[Pasted image 20241202095829.png]]

---
#### Approccio semantico

- Il **dominio di osservazione** è lo stesso dell'approccio algoritmico
	![[Pasted image 20241202100526.png]]
- **Funzione Semantica** è distributiva
	![[Pasted image 20241202101256.png]]
- **Soluzione finale MOP** 
	![[Pasted image 20241202101505.png]]
- **Sistema di disequazioni MFP**
	![[Pasted image 20241202102143.png]]
#### :LiExternalLink: REFERENZE: