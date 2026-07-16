#### :LiCalendarClock:  24/10/2024 - 15:59

#### Ricorsione
Di base il [[LAMBDA-CALCOLO]] non supporta le iterazioni e tanto meno le ricorsioni. Per ricorsioni intendiamo l'idea di definire oggetti/cose in termini di se stesse (fattoriale,fibonacci). Una ricorsione è composta da:

- caso base (fine chiamata ricorsiva)
- chiamata ricorsiva
#### Fixpoint (Turing-combinator)

Prima di defnire la ricorsione dobbiamo capire il fixpoint (punto di invarianza).

Il Fixpoint $p$ di una funzione $f$ è un punto che è mappato per se stesso 
$$
f(p) = p
$$ Se passiamo come argomento di $f$ il punto $p$, la funzione ci restituisce lo stesso punto $p$. Ecco perchè la ricorsione nel $\lambda$ calcolo ha bisogno del fixpoint, perchè abbiamo necessità che dato in argomento una funzione ad una funzione, quest'ultima ci restituisce la stessa funzione, appunto la nostra chiamata ricorsiva

L'idea chiave quindi è ==**applicare la funzione a se stessa**==
Esempio con $\lambda$ calcolo

![[Pasted image 20241024164334.png]]

Alan turing ci ha già definito due termini che esprimono la ricorsione in modo formale con approccio CBN:

![[Pasted image 20241024164603.png]]

- A: costrutto arbitrario
- FIX: alla fine sarà una funzione ricorsiva. è un funzionale, cioè prende una funzione di un certo tipo e ritorno la funzione dello stesso tipo. Restituisce quindi il punto fisso di quel funzionale
- M: è il funzionale, fix M è un punto fisso di M
- M(fix m): se M è un funzionale ritorna fix M $M(\text{fix m}) = \text{fix m}$ (come la definizione di punto fisso $f(p) = p$)

piccola dimostrazione punto fisso
![[Pasted image 20241024230047.png]]

Se M è un funzionale, allora la si può scrivere in modo più precisa, si può scrivere come una funzione che presa in input una funzione ritorna un'altra funzione. Siamo sempre in modalità CBN

![[Pasted image 20241030100855.png]]

esempio 

![[Pasted image 20241030102343.png]]

Questo meccanismo non funziona con l'approccio CBV

![[Pasted image 20241030103810.png]]

La soluzione è quello di portare il punto fisso di M come output di una $\lambda$ astrazione

![[Pasted image 20241030105834.png]]

#### Estensione del linguaggio

![[Pasted image 20241030110454.png]]

Ora avendo approdato che l'operatore FIX funziona possiamo anche eliminare il while volendo (perchè intrinsicamente è ricorsiva)

![[Pasted image 20241030111617.png]]

#### :LiExternalLink: REFERENZE: https://www.youtube.com/watch?v=9T8A89jgeTI