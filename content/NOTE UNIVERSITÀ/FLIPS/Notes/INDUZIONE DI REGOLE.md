#### :LiCalendarClock:  17/10/2024 - 16:32

Nell'induzione strutturale abbiamo un problema di fare induzione sulle espressioni del nostro linguaggio, perchè il loro valore potrebbero essere modificato(l'induzione strutturale si occupa di strutture sintattiche iterabili (grammatiche).

Può avvenire che semanticamente il comportamento delle espressioni aritmetiche è determinato dai comportamenti delle sotto espressioni.

Questo aspetto non può essere catturato dall'induzione strutturale.

Per questo ci viene in aiuto l'induzione di regole

L'idea è quella di ignorare la struttura degli oggetti e invece concentrasi sugli di derivazioni in cui una proprietà è stata derivata

#### Definizione formale
é come quella per induzione strutturale.
Per provare una proprietà P(D) per ogni derivazione di D, servono due condizioni:
- ==**CASO BASE**== provare se la proprietà P(A) è vera per ogni assioma di A
- ==**CASO INDUTTIVO**== per ogni regola che non sia un'assioma dimostrare che ogni derivazione finisce con l'uso delle regole in questione soddisfi la proprietà. Perchè queste derivazioni sono composte da sotto derivazioni che avranno delle conclusioni, e quindi per ipotesi induttiva assumere che P(Di) è vera per tutte le sotto derivazioni  
#### :LiExternalLink: REFERENZE: