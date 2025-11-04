#### Data: 05/02/2025 - 17:15

l'obbiettivo della t-closeness estende il concetto della [[K-Anonymity]] misurando la distanza della distribuzione di valori sensibili tra classi di equivalenza e il database originale

![[Pasted image 20250205172311.png]]
avendo come dati sensibili salario e malattia, avremo quindi k = 3 e L = 3

![[Pasted image 20250205172427.png]]

Il calcolo avviene in questo modo

1. **Calcolo della distribuzione globale**:
	Si determina la distribuzione complessiva dei valori dell’attributo sensibile su tutto il dataset.
	![[Pasted image 20250205173903.png]]
2. **Calcolo della distribuzione locale**:
	Si calcolano le distribuzioni degli attributi sensibili per ogni classe di equivalenza.
3. **Misurazione della distanza**:
	Si utilizza una metrica come l’**Earth Mover Distance** per quantificare quanto la distribuzione locale di ogni classe di equivalenza si discosta dalla distribuzione globale.
	![[Pasted image 20250205173850.png]]
	Per farlo dobbiamo associare ad ogni dato di ogni classe di equivalenza dei numeri casuali nella distribuzione originale (minimizzando la distanza) e fare la differenza tra di loro
	![[Pasted image 20250205175033.png]]
	 Dividiamo il tutto per n - 1
	 ![[Pasted image 20250205175115.png]]
	 Dividiamo ancora ma per 1/9 in questo caso perchè c'è solo bisogno di muovere un nono di probabilità di massa, siccome ogni elemento ha la stessa probabilità di apparire nella distribuzione (1/9)
	![[Pasted image 20250205175409.png]]
	![[Pasted image 20250205175451.png]]
	l'optimal mass flow ci dice quanto siamo vicini alla distribuzione originale
	![[Pasted image 20250205175547.png]]
4. **Confronto con la soglia t**:
	Se la distanza calcolata per ogni classe è inferiore o uguale a una soglia definita  t , il dataset soddisfa il criterio di **t-closeness**.

Si possono presentare situazioni in cui si ha a che fare con una distribuzione con elementi categorici e non numerici
![[Pasted image 20250205180056.png]]
![[Pasted image 20250205180126.png]]
#### REFERENZE: https://www.youtube.com/watch?v=Upb8jqlsbFM