Partendo da un sistema di due coordinate
![[Pasted image 20250503113655.png]]

si possono effettuare delle trasformazioni moltiplicando per un vettore a due dimensioni, uno dei problemi di fondo e di usare le trasformazioni staccandosi dal punto di origine che si può fare solo con traslando con un vettore di traslazione

![[Pasted image 20250503114131.png]]

Un approccio diverso è quello di aggiungere un'altra coordinata impostata ad 1 nel vettore e aggiungere una riga e colonna nella matrice da moltiplicare

![[Pasted image 20250503114114.png]]

ora piazzando il vettore traslazione nella parte in alto a destra della matrice possiamo ottenere lo stesso risultato

![[Pasted image 20250503114423.png]]
![[Pasted image 20250503114457.png]]

Quello che fa la differenza è che se si volesse applicare una trasformazione non servirebbe più il vettore, ma solo la moltiplicazione tra matrice di trasformazione e punto in input 

![[Pasted image 20250503114719.png]]

un altro vantaggio è che la coordinata omogenea fosse impostata a 0 il vettore viene "blocatto"

![[Pasted image 20250503114823.png]]
![[Pasted image 20250503114933.png]]
Questo viene utilizzato per i vettori, perchè il loro utilizzo interessa soltanto la direzione

Quindi tutte le nostre trasformazioni d'ora in poi si codificheranno attraverso delle matrici con coordinate omogenee e per i punti la coordinata omogenea è 1 mentre se si tratta di un vettore è 0

![[Pasted image 20250503151021.png]]