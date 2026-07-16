per specular intendiamo i riflessi speculari che percepisce l'osservatore quando l'oggetto è illuminato da una sorgente di luce, quindi oltre alla luce diffusa abbiamo un altra componente che definisce come l'oggetto riflette la luce che gli arriva

![[Pasted image 20250529095520.png]]

![[Pasted image 20250529094939.png]]

la regione in bianco viene chiamato lobo speculare e può variare in base all'orientazione della superficie e la posizione della sorgente di luce.

I riflessi alla fine però dipendono intrinsecamente dal materiale dell'oggetto, ad esempio un materiale metallico rifletterà più luce rispetto ad un materiale legnoso


---
### computazione riflessione

Il riflesso dipende da un'altra cosa, la posizione dell'osservatore, quindi ci serve un altro vettore che rappresenta la direzione vista e determinerà l'importo di luce di speculare in un certo punto

![[Pasted image 20250529100102.png]]

Ci sono tanti modi per implementare il modo con cui un oggetto riflette le luci, per il momento si usa il phong specular reflection

![[Pasted image 20250529100456.png]]

Per primo riflettiamo vettore $\omega$ che risulterà nel vettore $r$ che lo troviamo con la seguente formula

![[Pasted image 20250529104038.png]]


quello che ci interessa è l'angolo tra $r$ e $v$ 

![[Pasted image 20250529100909.png]]

l'ammontare di luce riflessa è determinata quindi dalla seguente formula

![[Pasted image 20250529101135.png]]

con $\alpha$ che indica il grado di lucentezza desiderato
Aggiungendo ora la specularità intrinseca di un oggetto la formula diventa

![[Pasted image 20250529101426.png]]
 
Un'altra cosa che dipende la riflessività di un oggetto è l'intensità di luce

![[Pasted image 20250529101613.png]]

