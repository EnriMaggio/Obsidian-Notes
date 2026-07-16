Il criterio più forte, che richiede di coprire tutti i percorsi possibili. Tuttavia, è noto che è spesso impossibile nella pratica raggiungere la copertura totale, a causa della "Path explosion" (esplosione dei percorsi nei loop, in pratica il numero di path è facilmente indefinito.

![[Pasted image 20260122155039.png]]
In questi casi si definice il path limitig, ovvero un upperbound sul numero di cicli da iterare, riducendo di molto il numero di path da attraversare.

Un altro problema di questo tipo di copertura sono i "percorsi ineseguibili" (codice logicamente irraggiungibile per certe combinazioni di input).

![[Pasted image 20260122155344.png]]Il percorso in rosso non è fattibile e mai eseguibile, perchè non esiste nessun numero $a$ che sia minore di 1 e maggiore di 4 allo stesso momento.

La copertura MCC non implica la all path coverage.
La all path coverage non implice la MCC coverage. 