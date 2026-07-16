La vista nelle applicazioni grafiche funziona in modo differente dalla vista umana, questo perchè gli umani hanno due occhi con cui possono determinare profondità e percezione. In OpenGl ad ogni run del vertex shader si aspetta che le coordinate siano all'interno di un range e qualsiasi coordinate al di fuori di questo range viene scartato, questo scarto viene chiamto Clipping. Quelli che restano diventeranno di conseguenza dei frammenti

Alal fine nello spazio clip vale solo che la scena compresa tra -1 e 1 in ciascuna coordinata è inquadrata nell'immagine

![[Pasted image 20250509101309.png]]

Può succedere che certi oggetti stiano a cavallo tra spazio interno ed esterno

![[Pasted image 20250509101550.png]]

Siccome è la fase in cui bisogna proiettare sul mondo 2d dobbiamo applicare la matrice projection che specifica il range di coordinate ammesse in ogni  dimensione, di seguito converte le coordinate in NDC (atttraverso la percezione)

Ma siccome siamo ancora in 3d le coordinate ammesse sono nel 3d, quindi abbiamo bisogno di una specie di cono o piramide in cui saranno visibili queste coordinate

Questo spazio viene definito viewing box (o frustum di vista) che è uno spazio tridimensionale definito dalla **matrice di view** e delimita ciò che si vede sulla spazio mondo 3D. Tutti i vertici/oggetti/elementi che rientrano in questo "cono" verranno disegnati e renderizzati a schermo la percezione)

