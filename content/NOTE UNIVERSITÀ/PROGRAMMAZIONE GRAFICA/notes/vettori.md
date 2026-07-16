
---
### Cosa è

Un **vettore** è un ente matematico caratterizzato da un'intensità (detta modulo) indicata dalla lunghezza del segmento, una direzione rappresentata dal segmento, e un verso indicato da una freccia.

È una freccia che parte da un punto e arriva a un altro dove c'è la punta della freccia

![[Pasted image 20250502102158.png]]

Il vettore rappresenta uno spostamento nello spazio ed ha una lunghezza e direzione.

Bisogna distinguerlo dal punto che invece rappresenta una posizione nello spazio 

![[Pasted image 20250502103157.png]]
![[Pasted image 20250502103209.png]]

il vettore in computer grafica è composto da 3 coordinate (per il mondo 3D quindi x,y,z)

![[Pasted image 20250502150732.png]]


---
### Lunghezza

per ricavare la lunghezza o il magnitudo di un vettore si può usare il teorema di pitagora. Un vettore in 2D (ma anche in 3d) forma un triangolo quando si cerca di visualizzare il componente x e y del vettore stesso come i 2 lati del triangolo e la freccia del vettore v come l'ipotenusa dello stesso triangolo 

![[Pasted image 20250502151440.png]]

siccome sappiamo la lunghezza dei lati con il teorema di pitagora possiamo trovare $\vec{v}$
attraverso la sua formula

![[Pasted image 20250502151754.png]]

$||\vec{v}||$ è la lunghezza del vettore. in 3D sarebbe

![[Pasted image 20250502152630.png]]

C'è un vettore speciale che si chiama vettore unitario, ovvero tutti quei vettori che hanno lunghezza 1, si può calcolare questo vettore da qualsiasi altro vettore non unitario semplicemente dividendo per ogni componente del vettore la lunghezza di quest'ultimo, questa operazione viene detta normalizzazione

![[Pasted image 20250502153142.png]]

Questo vettore nuovo è un puro indicatore di direzione, in un contesto grafico serve per la direzione senza preoccuparsi della scala 



si possono definire [[operazioni con i vettori]]