Questo spazio fa riferimento a quello che si chiama camera che si muove in maniera rigida rispetto al mondo in OpenGl. L'obiettivo di questa camera è quello di trasformare le coordinate dello spazio mondo in coordinate che sono piazzate di fronte alla vista dell'utente.

![[Pasted image 20250508162212.png]]

È quindi lo spazio che viene percepito, visto dal punto di vista della camera

Si può ottenere questo risultato con la matrice view

Lo spazio vista è situato in modo standard rispetto alla pin-hole camera che inquadra la scena. Le componenti della camera sono

![[Pasted image 20250508162450.png]]
![[Pasted image 20250508162721.png]]
(z+ è diretto verso lo schermo (noi), mentre z- è rivolto verso la scena)
![[Pasted image 20250508164053.png]]
La view riflette quindi la posizione e l'orientamento della camera (parametri estrinseci della telecamera) che inquadra la scena, ovviamente ogni spostamento della camera cambierà valori di questa matrice di vista

[[costruzione matrice view]]
[[costruzione matrice perspective]]
[[muovere camera]]