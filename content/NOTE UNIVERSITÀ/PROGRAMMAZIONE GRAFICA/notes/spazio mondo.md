Trasportando gli oggetti da sistema locale al sistema mondo, è molto probabile che questi soggetti saranno spostati, in base a preferenze, all'interno di un mondo più grande, ad uno spazio comune a tutta la scena 3D, altrimenti tutti staranno nella posizione (0,0,0)

Per farlo bisogna applicare la matrice di trasformazione model, model perchè modella il contenuto della scena. La trasformazione può essere di traslazione, scalatura e rotazione, ma anche una combinazione di questi

Adesso le coordinate dell'oggetto saranno relative rispetto a questo spazio nuovo.
Da tener conto che ogni oggetto da portare al nuovo spazio dovrà avere la sua trasformazione di modellazione 

![[Pasted image 20250508161442.png]]
(in questo esempio lo stesso oggetto coniglio ha quattro istanze, ogni istanza però è modellato da una propria matrice model)
![[Pasted image 20250508161535.png]]

La divisione fra coordinate oggetto e mondo è utile anche per risparmiare memoria, come appena visto in memoria posso tenere un oggetto e istanziarlo più volte 
![[Pasted image 20250508154923.png]]

![[Pasted image 20250508160900.png]]
![[Pasted image 20250508160933.png]]