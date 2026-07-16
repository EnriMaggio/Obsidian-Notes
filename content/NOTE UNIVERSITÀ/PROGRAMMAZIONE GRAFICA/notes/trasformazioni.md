Nel contesto della programmazione grafica, le **trasformazioni spaziali** sono operazioni fondamentali che permettono di modificare la **posizione**, l’**orientamento** e la **scala** degli oggetti nello spazio.

più precisamente le trasformazioni sono funzioni che applico a dei punti in input e che restitueranno altri punti in output

a seconda della trasformazione certe proprietà vengono mantenute o perse

![[Pasted image 20250503105855.png]]

A livello concettuale, le trasformazioni agiscono su punti e vettori utilizzando strumenti matematici come **matrici** e **vettori omogenei**, permettendo di comporre più operazioni in modo efficiente.

Le trasformazioni principali fanno uso di [[coordinate omogenee]] sono:

- [[traslazione]]: sposta un oggetto da una posizione a un’altra.
- [[rotazione]]: cambia l’orientamento di un oggetto intorno a un asse.
- [[scala]]: ingrandisce o riduce le dimensioni di un oggetto.

Capire come queste trasformazioni agiscono sullo spazio e come combinarle correttamente è essenziale per gestire il movimento, le camere, le luci e gli oggetti in una scena grafica.

Sono importanti anche le matrici inverse, in algebra le matrici inverse sono le trasposte, queste matrici servono alla fine per annullare o invertire una trasformazione

ci sono anche delle [[trasformazioni affini]]

i vettori che codificano una coordinata spaziale sono punti
i vettori che indicano una direzione sono vettori veri e propri