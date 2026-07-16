#### :LiCalendarClock:  16/10/2024 - 12:12

Quando si definisce un linguaggio di programmazione c'è il bisogno di creare strutture all'interno del nostro codice che possono essere funzioni, metodi o procedure.
Nel nostro caso estenderemo il nostro linguaggio con funzioni [[High Order]] che prenderanno valori o funzioni e che ritorneranno valori o funzioni (nei linguaggi funzionali saranno valori)
 ecco degli esempi:
#### Sintassi funzioni
![[Pasted image 20241016124400.png]]
([[Spiegazione funzione successore applicata due volte]])
Ora possiamo estendere la sintassi con queste funzioni:

![[Pasted image 20241016153541.png]]
#### Comportamento variabili
![[Pasted image 20241016160330.png]]
Il problema delle variabili locali e parametri formali è che possono avere lo stesso nome anche se hanno significati diversi.
Per questo c'è il **Variable shadowing**, ovvero definire ambienti in cui possiamo mettere lo stesso nome di più variabili e che si possono riutilizzare nomi di variabili già utilizzati
![[Pasted image 20241016160240.png]]
![[Pasted image 20241016161623.png]]
Un'aspetto da considerare sono le variabili libere e legate
![[Pasted image 20241016162123.png]]

Con l'alpha conversion possiamo permetterci di fare
![[Pasted image 20241016162910.png]]

#### Variabili libere
Formalmente è una funzione che presa un'espressione ne tira fuori le sue variabili libere
![[Pasted image 20241016163652.png]]
Il problema nasce più che altro quando ai parametri formali passiamo delle variabili (quindi con nome) al posto delle costanti. Esempio di sostituzione
![[Pasted image 20241022112646.png]]

La sostituzione è definita per induzione strutturale sugli elementi del linguaggio while

![[Pasted image 20241022113639.png]]
![[Pasted image 20241022112924.png]]

La sostituzione può essere generalizzata per rimpiazzare più variabili simultaneamente. C'è differenza se provassimo fare una sostituzione passo passo perchè potrebbe causare problemi con le ambiguità dei nomi delle variabili
#### :LiExternalLink: REFERENZE: