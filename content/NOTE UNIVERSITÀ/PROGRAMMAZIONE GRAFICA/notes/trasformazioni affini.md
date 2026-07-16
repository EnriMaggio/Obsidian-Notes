sono trasformazioni che possono essere codificate in una matrice 4x4, le trasformazioni viste fino ad ora fanno parte di questa categoria.

Queste trasformazioni sono importanti perché preservano alcune proprietà geometriche 
### Cosa preservano:
 
- **Colinearità**  
    Se più punti giacevano su una stessa retta, continueranno a farlo anche dopo la trasformazione. È importante perché si può trasformare un triangolo 3d in uno 2d trasformando i suoi tre vertici e connettendo i vertici trasformati
- **Rapporti tra distanze di punti colineari**  
    Ad esempio, il punto medio di un segmento resta il punto medio anche dopo la trasformazione.
- **Parallelismo tra rette**  
    Due rette parallele restano parallele anche dopo la trasformazione.


### Tipi di trasformazioni affini
Alcune tipi di trasformazioni sono:
- __Isometriche__
	mantengono le distanze fra punti
- __Conformali__
	mantengono gli angoli fra i vettori
- __Volume__
	mantengono i volumi
- __Invertibili__
	se esiste la trasformazione opposta

### Matrice 4x4

La base di partenza di una trasformazione affine è questa per i punti
![[Pasted image 20250504154942.png]]
mentre per i vettori è questa
![[Pasted image 20250504155201.png]]

Questa matrice la si può suddividere in quattro parti 
![[Pasted image 20250504155628.png]]

Alcune matrici affini sono la identità che quindi trasforma ogni punto o vettore in se stesso, e la matrice inversa se esiste

Una matrice affine è chiusa per composizione, ovvero che se si applicano due trasformazioni affini uno dopo l'altra il risultato è ancora affine. 
La moltiplicazione va da destra a sinistra tra trasformazioni, ma con un punto la moltiplicazione è associativa

![[Pasted image 20250504160134.png]]

questo ci fa capire che possiamo applicare una trasformata ad un punto rispetto che calcolare per ogni punto una sola trasformata e poi calcolarne per un'altra, con tanti punti conviene fare il prodotto tra trasformazione finale e poi moltiplicare per tutti i punti

Bisogna stare attenti a fare l'inversa di un prodotto tra matrici  affine e generica
![[Pasted image 20250504160748.png]]
![[Pasted image 20250504160755.png]]