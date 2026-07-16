
---
### Rotazione 2D

In 2d la rotazione di un vettore avviene così

![[Pasted image 20250503170837.png]]

![[Pasted image 20250503171758.png]]
questa è una matrice che permette di ruotare in senso antiorario, se si vuole ruotare in senso orario basta mettere l'angolo negativo


---
### Rotazione 3D

il grafico cartesiano in 2d nasconde in verità il terzo asse, ovvero z
![[Pasted image 20250504113952.png]]

E la rotazione in 2d che abbiamo visto prima non è altro con l'asse di z fissato, ovvero che non cambierà nessun punto z, quindi aggiungendo una terza riga e colonna nella diagonale rimmarrà 1

![[Pasted image 20250504114125.png]]

A questo punto si può ruotare anche rispetto agli altri assi

![[Pasted image 20250504114218.png]]

L'asse fissato avrà la sua coordinata rispettivamente ad 1 perchè non deve cambiare 

Bisogna sempre specificare quale è l'asse di rotazione e questa trasformazione si può applicare ai punti e sia ai vettori e i punti che sono sull'asse vengono mappate su se stessi

Attenzione che le rotazioni non sono commutative tra di loro e con altre trasformazioni

![[Pasted image 20250504122930.png]]

Una proprietà interessante di questa matrice di rotazione è che è ortogonale(ortonormale), ovvero la sua inversa corrisponde alla matrice trasposta, infatti se si moltiplicano queste 2 si ottiene la matrice identità

Inoltre essendo ortonormale le righe e colonne sono vettori con norma 1

Algebricamente è cosi, oppure l'inversa di una matrice di rotazione è semplicemente l'angolo negato

![[Pasted image 20250504124256.png]]

La matrice di rotazione si distingue da altre matrici ortonormali nella sua determinante che può essere  uguale a 1 o a -1

L'effetto geometrico di questa determinante è che mantiene le proporzioni dell' oggetto che si sta ruotando

