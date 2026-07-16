#### :LiCalendarClock:  03/12/2024 - 16:10
---
#### INTRODUZIONE

A differenza della analisi statica DataFlow, l'interpretazione astratta si concentra di più sui ==**valori**== degli stati della macchina, se si riesce a dare una semantica, quest'ultima non sarà distributiva, quindi ci distaccheremo dalle soluzioni MOP o MFP (perdendo precisione).

Ora si entrerà in un mondo in cui abbiamo bisogno di strumenti costruttivi sofisticati per formalizzare la semantica, ed essendo strumenti che passo passo definiscono l'analisi sugli oggetti osservati non andremo a dimostrare matematicamente questi strumenti, ci basta solo che siano [corretti](SOUNDNESS)

L'interpretazione astratta è un ==framework formale== ha come obiettivo finale la formalizzazione in modo dettagliato della ==relazione== tra il mondo concreto e il mondo astratto, infine riuscire a trasferire la risposta dal mondo astratto al mondo concreto

- nel mondo concreto non riusciamo a dare una risposta decidibile secca ma di cui vogliamo dire qualcosa
- nel mondo astratto o approssimato riusciamo a dire qualcosa

---
#### SPIEGAZIONE GRAFICA IDEA

Supponiamo di avere un oggetto che è un coppia formata da:
- un punto di origine x (fulcro dell'oggetto)
- un insieme finito di pixel neri 

![[Pasted image 20241203164352.png]]

Ora consideriamo nel nostro dominio un oggetto di tipo fiore e lo andiamo a considerare come una sequenza di operazioni che noi andiamo ad applicare ad elementi più piccoli

![[Pasted image 20241203164944.png]]

delle operazioni per formare il fiore sono:
- oggettino costante petalo (con il suo fulcro e i suoi pixel)
- operazione di rotazione su un oggetto sul suo fulcro (funzione che preso un angolo ruota l'oggetto)
- operazione di unione degli insiemi di pixel di vari oggetti sovrapponendo le origini dei vari oggetti
- operazione di gambo, aggiunge un nuovo fulcro che si collega con quello vecchio

![[Pasted image 20241203165542.png]]
![[Pasted image 20241203165926.png]]
![[Pasted image 20241203170819.png]]

Possiamo calcolare per punto fisso la corolla con un operatore monotono

![[Pasted image 20241203171146.png]]

Un ultima operazione è il bouquet, ovvero un'insieme di fiori

![[Pasted image 20241203171622.png]]
Abbiamo introdotto un dominio concreto, sul quale vorremo poter dare delle proprietà, di oggetti su cui abbiamo definito le operazioni

---
#### ASTRARRE (OVER APPROXIMATION)

Per dare una risposta dobbiamo essere meno precisi e approssimare il dominio concreto, per farlo dobbiamo avere la stessa origine e più pixel per ==astrarre== un oggetto nel dominio concreto, che significa aggiungere rumore perdendo informazioni

![[Pasted image 20241203173604.png]]

==L'oggetto astratto== è una rappresentazione di un oggetto concreto in forma approssimata, avviene un _"rilassamento"_ del contorno (perimetro) che allarga i _"limiti"_ dei pixel dell'oggetto originale attraverso una _"penna"_ con un tratto molto più grande che cerca di _"ricalcare"_ il contorno originale, in modo che li contenga

![[Pasted image 20241203173710.png]]

Infine avendo due domini, uno concreto e uno astratto, ci sono due operatori di trasformazione:

- $\alpha$ che mi permette di astrarre un oggetto concreto che lo rappresenti nel nuovo dominio
- $\gamma$ che descrive il significato concreto di un oggetto astratto

Infatti ci servirà un qualcosa per tornare indietro dal dominio astratto a quello concreto
![[Pasted image 20241203174825.png]]

---
#### CONCRETIZZAZIONE

Oltre ad astrarre (che ci ha permesso di creare nuovi oggetti basati sul dominio concreto), dobbiamo ==assegnare un significato concreto== dell'oggetto astratto che stiamo osservando.

Nel caso dei fiori l'idea è quello di riempire il contorno internamente con pixel neri, in modo da catturare tutti gli oggetti possibili all'intero di quel perimetro

Questo di fatto è come aggiungere rumore, la imprecisione che ci dobbiamo sorbire per dare una risposta nel mondo astratto per poi darlo nel mondo concreto, l'oggetto concreto sarà compreso nel rumore

![[Pasted image 20241203175529.png]]

ad esempio l'astrazione dei numeri pari su un oggetto finito {2,6} è {2Z} che corrisponderà al contorno, la sua concretizzazione sarà l'insieme che conterrà tutti i numeri pari 

L'astrazione è collegata con la concretizzazione con la [connessione di galois](https://it.wikipedia.org/wiki/Teorema_fondamentale_della_teoria_di_Galois) descrivendo il fatto che $\alpha$ e $\gamma$ sono funzioni monotone, ovvero non cambiano l'ordinamento degli elementi tra i due domini.

![[Pasted image 20241203180700.png]]
![[Pasted image 20241203180728.png]]

Dobbiamo ora trasferire le operazioni dal mondo concreto al mondo astratto
![[Pasted image 20241204121253.png]]
bisogna prima quindi concretizzare e svolgere le operazioni, per poi astrarre

![[Pasted image 20241204122009.png]]
#### :LiExternalLink: REFERENZE: