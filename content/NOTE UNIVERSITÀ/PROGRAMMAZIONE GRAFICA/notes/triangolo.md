![[Pasted image 20250320150609.png]]

il triangolo nella programmazione grafica è l'elemento di base per costruire una superficie di un modello 3D e quindi può essere usato per creare tutto ciò che pensiamo

Per realizzare un oggetto più realistico possibile servono tanti triangoli, questo però porta un costo significativo alla performance

![[Pasted image 20250320152801.png]]


![[Pasted image 20250320150514.png]]


---
#### TRIANGOLO VISTO DAL COMPUTER

Un triangolo è quindi composto da

- **vertici (V)**
	un triangolo ha 3 vertici, ogni vertice è rappresentato nello spazio 3D con coordinate (x,y,z)
- **archi (E)**
	sono i segmenti che uniscono i vertici
- **Una normale (N)**
	Un vettore perpendicolare alla superficie, usato per l'illuminazione e gli effetti di shading.

questi sono fondamentali per costruire un triangolo per i nostri modelli, ma ci sono altre informazioni di interesse che possono essere aggiunte

- **Texture Coordinates (UV Mapping)**
	Coordinate che associano una texture all'oggetto.
- **Colori per vertice**
	Permettono effetti come il gradient shading.
- **Peso dei vertici** (nei modelli animati)
	Per deformazioni fluide con scheletri (rigging).

con un triangolo si può iniziare a fare la [[mesh triangolare]]

