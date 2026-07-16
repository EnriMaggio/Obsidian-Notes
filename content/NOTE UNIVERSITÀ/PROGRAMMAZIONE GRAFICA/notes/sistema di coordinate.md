Quando vogliamo disegnare un oggetto 3D sullo schermo 2D, dobbiamo portarlo attraverso una serie di trasformazioni tra diversi sistemi di riferimento (o coordinate systems). Ogni passaggio ha uno scopo preciso nella visualizzazione della scena e comporta una sotto trasformazione che può essere vista come un cambio di sistema di riferimento.
[[sistema di coordinate in opengl]]

ci sono 5 sistemi di coordinate(riferimento):
1. [[spazio locale]]
2. [[spazio mondo]]
3. [[ spazio vista]]
4. [[spazio clip]]
5. [[spazio schermo]]

Per passare da un sistema all'altro si applicano trasformazioni di matrici

![[Pasted image 20250508153931.png]]

![[Pasted image 20250508133718.png]]

Queste sono tutti sistemi di coordinate in cui i vertici vengono trasformati per poter alla fine generare i frammenti

![[Pasted image 20250510171114.png]]