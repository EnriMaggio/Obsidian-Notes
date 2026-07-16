Una volta creato l'oggetto si ha la necessità di spostarlo o posizionarlo in un certo modo all'interno di una scena, quindi oltre alle coordinate dei modelli abbiamo bisogno di coordinate dei modelli nella scena (mondo), quest'ultime coordinate si ottengono trasformando le coordinate dei modelli attraverso calcoli con le matrici

di un modello si può modificare quindi
- posizione
- orientamento
- scala nello spazio tridimensionale

Le trasformazioni 3D più comuni sono:

1. [[traslazione]]
2. [[rotazione]]
3. [[scala]]
4. Trasformazioni Composte (Combination of Transformations)**

Queste trasformazioni vengono applicate ai **vertici** di un modello utilizzando **matrici di trasformazione** da 4×4, che operano nel sistema di coordinate omogenee.

![[Pasted image 20250320214800.png]]