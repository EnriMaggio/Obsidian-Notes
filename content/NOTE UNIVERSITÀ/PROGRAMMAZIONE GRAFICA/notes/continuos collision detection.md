![[Pasted image 20250715093037.png]]

l'interpolazione lineare è come se fosse la media pesata tra i punti di partenza e arrivo.
L'obiettivo della collisione continua è quella di riempire le informazioni mancanti tra i frame.

La prima parte della collisione continua è come trovare il punto esatto della collisione (in questo caso una linea orizzontale) con dei vincoli in gioco.

Un vincolo in questo caso è il centro della particella che dista $r$ dalla retta orizzontale, con $r$ il raggio della particella

![[Pasted image 20250715093619.png]]

abbiamo quindi questa relazione

![[Pasted image 20250715093914.png]]

poi possiamo combinare il vincolo formalizzato con l'interpolazione lineare e otteniamo un sistema di equazioni linari (sostituendo  $y(t_c)$ nella seconda equazione) con variabile $t_c$ ovvero il tempo di collisione

![[Pasted image 20250715094053.png]]
![[Pasted image 20250715094751.png]]
(in questo esempio $t_c = 0.23$)

la seconda parte della collisione continua è qulla di capire il cambio di traiettoria della particella dopo la rilevazione della collisione. Sempre in questo caso basta flippare, negare la componente y

![[Pasted image 20250715095035.png]]

non è sempre facile usaree la rilevazione di collisione continua a causa di:

- complessità geometrica
- contesto
- distanze
- dimensioni multiple
- algoritmi per trovare il root