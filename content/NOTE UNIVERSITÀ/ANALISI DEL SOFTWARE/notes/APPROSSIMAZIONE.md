#### Data: 08/10/2024 - 11:12
#### Stato: #inProgress
#### Tags: [[SOUNDNESS]],[[COMPLETENESS]]

C'è un'accettazione di risposte non precise, quindi si approssimano risultati non sbagliati, ma accurati.
Avere una ==**risposta precisa**== significa:
$$
∀p∈L, analisi(p)=true⟺
\text{ p soddisfa }
\pi
$$
Questa formula ci dice che per ogni programma se l'analisi risulta vera, allora il programma soddisfa la proprietà (idealmente)
Nella realtà quando dobbiamo ==**approssimare**== dobbiamo indebolire il concetto di se e solo se ($⟺$)
![[Pasted image 20241008112341.png]]
Questa immagine in sostanza ci dice che se l'analisi del programma p è true allora sta nel riquadro di sinistra, a destra se è false. Quando dobbiamo rilassare abbiamo il concetto di ==**soundness e completeness**==
