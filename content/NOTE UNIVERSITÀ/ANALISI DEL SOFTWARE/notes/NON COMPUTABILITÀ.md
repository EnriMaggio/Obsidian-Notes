#### Data: 08/10/2024 - 10:23
#### Stato: #inProgress
#### Tags: [[Teorema di Church-Turing]],[[Teorema di Rice]],[[SOLUZIONE ALLA NON COMPUTABILITA]]

Il limite principale dell'analisi è la ==**non computabilità**== (non calcolabilità). ==**Idealmente**== vorremo che, dato un linguaggio di programmazione che si può utilizzare per scrivere programmi e un insieme a delle proprietà, il nostro strumento di analisi calcolasse in ==**modo automatico**== il risultato esatto e preciso in tempo finito
Questo purtroppo non può avvenire in quanto stiamo trattando ==**macchine di Turing**==, quindi il problema della terminazione se avviene non è decidibile, ovvero implica che non esiste un programma che riesce a decidere la terminazione di un altro programma
ad esempio:
$$
∀p∈L, halt(p)=true⟺
\text{ p termina }
$$
questo non può esistere e per il teorema di rice non posso determinare in modo automatico proprietà non banali