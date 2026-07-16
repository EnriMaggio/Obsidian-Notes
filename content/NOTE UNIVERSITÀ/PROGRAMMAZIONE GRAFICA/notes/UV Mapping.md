Questa tecnica consiste nell'assegnare una coppia di coordinate textures ad ogni vertice della mesh, quindi oltre alle coordinate (x,y,z), quest'ultimo si estende con la nuova coppia (u,v) che vanno ad identificare un pixel della texture

l'oggetto 3D viene "srotolato"/ aperto come una cartina geografica su un piano, in pratica viene appiattita la mesh, a cui viene applicata direttamente la texture

A questo punto ogni vertice dell'oggetto tridimensionale disporrà di un set di coordinate bidimensionali condiviso con l'immagine, che potrà essere quindi associata alle sue facce, risultando visibile nello spazio 3D. Le coordinate UV fanno quindi da ponte tra lo spazio bidimensionale delle immagini (texture) e quello tridimensionale della mesh.

![[Pasted image 20250324140224.png]]

Il pixel con le nuove corrdinate diventa un texel

Un **texel** è un pixel su una texture. Un texel raramente si mappa in modo 1:1 su un pixel dello schermo. Il termine **texel**, abbreviazione di "texture element" (elemento di texture), rappresenta l'unità fondamentale di una texture nella grafica computerizzata. A differenza di un pixel, che corrisponde direttamente a un punto sullo schermo, un texel è un'unità discreta all'interno di una mappa di texture. Il rapporto tra texel e pixel dello schermo raramente segue una corrispondenza diretta uno a uno.