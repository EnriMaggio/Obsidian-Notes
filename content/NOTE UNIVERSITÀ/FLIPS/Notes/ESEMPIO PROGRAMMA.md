#### Data: 08/10/2024 - 22:47
#### Linked Notes: [[STORE]]

![[Pasted image 20241008224744.png]]
==**CONSIDERAZIONI**==
- Ci sono problemi in questo programma?
	C'è un problema con l1, o meglio bisogna stabilire/assumere che $l_1>0$
- Che valora avrà l3 a fine terminazione programma?
	il valore di $l_3$ sarà $l_3=l_2 - 1$, questo perchè se guardiamo l'inizio del programma notiamo che $l2 = 1$ e $l3=0$, quindi inizialmente $l_3$ è già indietro di $1$ da $l_2$. Quando si entra nel while questi due valori si aggiorneranno man mano finchè non si uscirà dalla guardia while, ma si aggiornano sempre incrementando di $1$, quindi $l_3$ rimarrà sempre indietro di 1 rispetto a $l_2$
- Che valora avrà l2 a fine terminazione programma?
	$l_2$ avrà lo stesso valore di $l_1$
- Che valora avrà l1 a fine terminazione programma?
	$l_1$ sarà $l1=l3+1$ (che non è altro il valore di $l_2$ quindi alla fine $l_1$)
Grazie alla operazione semantica fornita possiamo fornire una semantica formale a questo pezzo di codice. Sia
$$
[-] : Exp \rightarrow (Store \rightharpoonup Store)
$$ dato una $e \in Exp$, $[e]$ è una funzione parziale che trasforma la $Store$ iniziale $s$  in una $Store$ finale $s'$ 

![[Pasted image 20241009160640.png]]

Con questa definizione possiamo descrive la semantica operazionale di questo snippet di codice

![[Pasted image 20241009161030.png]]