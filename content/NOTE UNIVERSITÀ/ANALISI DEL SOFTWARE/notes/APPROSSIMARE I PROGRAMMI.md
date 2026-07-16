#### :LiCalendarClock:  23/10/2024 - 10:17

#### Problema di decibilità di una proprietà Q

Le proprietà $Q$ soddisfatte non sono altro che insiemi di esecuzioni di un programma che rispettano quella proprietà (in modo estensionale, quindi tutte le sue possibili esecuzioni)

Idealmente vorremmo dire che
$$
[P] \subseteq Q
$$ il problema è che questo non è decidibile ([[Teorema di Rice]])
#### Soluzione al problema

Siccome non possiamo soddisfare tutte le proprietà nel nostro programma, abbiamo bisogno di ==**approssimare**== i dati e le computazioni

Per approssimare si intende _"aggiungere rumore"_ alla semantica del nostro programma

Formalmente approssimeremo la semantica
 $$
[P]^{\#} \supseteq
 [P]
$$
Dove $P^{\#}$ è la semantica astratta/approssimata e rappresenta con un certo grado di errore la semantica concreta, la conterrà tutta. In aggiunta abbiamo il vincolo che
$$
[P]^{\#} \subseteq Q
$$ Ovviamente si deve costruire questa nuova semantica con lo scopo di soddisfare $Q$ che in questo caso invece sarà decidibile (per transitività)
$$
[P] \subseteq [P]^{\#} \subseteq Q
$$
#### Rappresentazione grafica della semantica astratta

![[Pasted image 20241023105716.png]]

Si capisce che abbiamo una risposta sicura solo nel caso in cui si soddisfa la proprietà, quando invece è no non possiamo dire sicuramente se Q non appartiene alle semantiche o che la proprietà è soddisfatta nella concreta ma non nella astratta

#### Come costruire la semantica astratta da quella concreta

Sappiamo che la semantica non è altro che un coppia
$$
[P] = (F,D)
$$ 
Astrarre la semantica allora è adattare a la computazione che abbiamo adottato sugli oggetti che abbiamo scelto di osservare

![[Pasted image 20241023111329.png]]

Quindi avremo una sorta di lente con dei _"filtri"_ che ci permette di individuare cosa vogliamo osservare con precisione, tutto ciò che noi non osserviamo la approssimeremo (aggiungendo errore)

esempio

![[Pasted image 20241023113333.png]]

Gli oggetti possibili che noi possiamo approssimare su un linguaggio di programmazione sono

![[Pasted image 20241023113520.png]]

 ed un esempio di proprietà, ovvero un insieme di oggetti che soddisfano le proprietà, sono
 
![[Pasted image 20241023113602.png]]

#### Caratteristiche del dominio delle proprietà sugli oggetti concreti

 ![[Pasted image 20241023115610.png]]

#### Approssimazione per difetto o eccesso

Avendo una proprietà concreta dobbiamo approssimarla in una proprietà astratta, ma dobbiamo scegliere in che direzione la semantica viene approssimata
- $\pi \subseteq \pi ^{\#}$ è più facile perché facciamo over approximation (eccesso)
	![[Pasted image 20241023122821.png]]
- $\pi ^{\#} \subseteq \pi$ è più difficile perché facciamo under approximation (difetto)
	![[Pasted image 20241023122846.png]]

#### Perché funziona
Funziona la proprietà astratta più grande perchè abbiamo scelto di guardare non direttamente tutti gli elementi, ma l'invariante con cui osserviamo gli oggetti concreti (con questo aggiungo tutti valori che riguardano l'invariante, ecco il rumore)

#### La migliore approssimazione
Non vogliamo che un certo elemento di $A$ approssimi per eccesso la proprietà concreta, alla fine vogliamo che $P^{\#}$ sia il più piccolo possibile e questo significa che è la migliore approssimazione di $P$. L'approssimazione deve associare ad ogni elemento concreto $P(D)$ il migliore elemento astratto che lo approssima

![[Pasted image 20241023162843.png]]
#### Esempio di approssimazione

Per prima cosa approssimiamo gli elementi
![[Pasted image 20241023164156.png]]

Poi approssimiamo le operazioni del programma (semantica astratta)

![[Pasted image 20241023164824.png]]

#### :LiExternalLink: REFERENZE: