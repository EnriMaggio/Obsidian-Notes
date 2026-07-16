#### :LiCalendarClock:  29/10/2024 - 09:42

---
#### OBIETTIVO DELLA ANALISI

Individua tutte le definizioni (assegnamenti) che raggiungono un punto di programma senza ridefinizioni intermedie

![[Pasted image 20250219095605.png]]

è molto utile per l'analisi di LOOP INVARIANT CODE MOTION

![[Pasted image 20250219100219.png]]

Serve per ottimizzare il codice nel caso una definizione non viene ridefinita, quindi piuttosto di rieseguire la stessa definizione n volte non ha senso, la si porta prima del ciclo e viene eseguita soltanto una volta

---
#### TIPO DI ANALISI

Siccome dobbiamo a vedere se ci sono ridefinizioni di definizioni già esistenti l'analisi è di tipo FORWARD, e siccome dobbiamo individuare tutte le definizioni allora dobbiamo unire tutti i cammini, cioè devo collezionarle tutte perchè può esserci la possibilità anche minima che le definizioni raggiungono un punto di programma, quindi è POSSIBLE


---
#### DOMINIO OSSERVATO

![[Pasted image 20250219101221.png]]


---
#### APPROCCIO ALGORITMICO

![[Pasted image 20250219103310.png]]


#### :LiExternalLink: REFERENZE: