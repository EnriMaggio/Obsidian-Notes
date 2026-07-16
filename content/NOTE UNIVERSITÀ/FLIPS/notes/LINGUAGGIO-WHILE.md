#### Data: 08/10/2024 - 22:37
#### Tags: 

Introduciamo la sintassi di questo linguaggio imperativo con locazioni di memoria, condizionali, while loops, tipi di valori. Questa sintassi è astratta, quindi la grammatica definirà alberi sintattici

![[Pasted image 20241008224545.png]]
ecco un [[ESEMPIO PROGRAMMA]] data questa sintassi
In questo linguaggio abbiamo bisogno però delle regole per ==**valutare le espressioni**== perchè da sintassi i numeri $\in \mathbb{N}$ vengono salvati in delle locazioni $\mathbb{L}$ e attravarso il simbolo $\text{!}$  andremo a dereferenziare la località $l$, ovvero andare a prendere il valore puntato da una località. La semantica operazionale deve tener conto di questa cose, ma per farlo ha bisogno di sapere lo stato della memoria della macchina/programma e lo faremo con la [[STORE]]
In seguito si descriverà la semantica operazionale di questo linguaggio [[SEMANTICA-WHILE]] 
L'esecuzione di un programma scritto con questo linguaggio è definito nel seguente modo 
$$
<P,s> \rightarrow^* <v,s'>
$$
Per eseguire un programma $P$ partendo da uno stato $s$ trovare lo stato $s'$ tale che il risultato sia $v$, ovvero un terminale v che $\in \mathbb{V} = \mathbb{B} \cup \mathbb{B} \cup \text{\{skip\}}$ 
il terminale può essere un booleano,intero o uno skip. Le configurazioni che terminano nella forma $<v,s>$ sono dette ==**terminali**== 
Questo linguaggio avrà delle [[PROPRIETA-WHILE]] in base al suo funzionamento e implementa diverse scelte di design [[DESIGN-WHILE]]
Una volta fatto ciò abbiamo un linguaggio che è Turing Completo ma che non ha supporto per funzioni, branching, oggetti ecc. ecc. Uno dei problemi di questo linguaggio è che manca un ==**sistema di tipi**==, ad esempio con questo linguaggio è possibili scrivere per il momento $3+true$ 
#### Nota successiva: [[SISTEMA DI TIPI]]