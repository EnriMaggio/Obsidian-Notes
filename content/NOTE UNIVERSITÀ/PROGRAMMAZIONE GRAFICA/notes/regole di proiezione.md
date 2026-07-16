c'è una proiezione
- **Ortografica**
	gli oggetti vengono mappati sul piano immagine senza una variazione di dimensione
	 ![[Pasted image 20250320220237.png]]
- **Proiettiva**
	si emula la fisica del sistema proiettivo (gli oggetti lontani sono più piccoli) usando matrici di proiezione percettiva che riescono a produrre un'immagine piatta partendo dai modelli 3d
	 ![[Pasted image 20250320220716.png]]
	di solito si deve definire il cono di vista (frustum), in pratica si cerca di realizzare un parallelepipedo all'interno di questa piramide, definendo il piano più vicino ovvero quello piccolo(che sarà lo schermo) e il piano più lontano ovvero quello grande, tutte le informazioni che non ricadono in questa sezione di parallelepipedo, cioè il view frustum, viene tagliato via e si chiama clipping