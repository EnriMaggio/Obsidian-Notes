L'architettura **MIMD** (acronimo di **Multiple Instruction, Multiple Data**, ovvero "Istruzioni Multiple, Dati Multipli") è la quarta categoria della tassonomia di Flynn e rappresenta **la tipologia di computer parallelo più diffusa in assoluto** al giorno d'oggi.

![[Pasted image 20260303122547.png]]

Ecco i dettagli del suo funzionamento:

- **Multiplo Flusso di Istruzioni (Multiple Instruction):** Il sistema è dotato di molteplici Unità di Controllo (CU) e Unità di Elaborazione (PU). Ogni processore preleva ed esegue il proprio flusso di istruzioni indipendente; questo significa che ogni processore può eseguire un programma o una porzione di codice completamente diversa dagli altri nello stesso momento.
- **Multiplo Flusso di Dati (Multiple Data):** Ciascun processore opera in parallelo lavorando su un proprio set di dati distinto da quello degli altri.

**Caratteristiche e Comportamento:**

- **Esecuzione Indipendente e Asincrona:** La differenza fondamentale rispetto alla classe SIMD (in cui l'esecuzione è rigorosamente sincronizzata istruzione per istruzione) è che nel modello MIMD i diversi software possono avanzare in modo totalmente indipendente l'uno dall'altro. Un'unità di calcolo può essere all'inizio del suo programma mentre un'altra è già arrivata alla fine. L'esecuzione, pertanto, può essere sia sincrona che asincrona, deterministica o non deterministica.
- **Indipendenza dei task:** Può essere visualizzato come l'equivalente di avere tanti software del tutto indipendenti che girano contemporaneamente sulla stessa piattaforma di calcolo distribuita su molteplici processori.
- **Natura Ibrida:** È interessante notare che la maggior parte delle architetture MIMD moderne non è "pura", ma include al proprio interno dei sub-componenti di esecuzione di tipo SIMD (ad esempio, i singoli core di una moderna CPU spesso includono unità in grado di processare istruzioni vettoriali SIMD).

**Esempi e Applicazioni:** La stragrande maggioranza dei computer moderni ricade esattamente in questa categoria. Tra gli esempi principali troviamo:

- I **moderni PC e computer portatili** dotati di processori multi-core (come ad esempio le architetture Intel IA32 o AMD Opteron).
- Le enormi infrastrutture basate su **cluster di computer** connessi in rete e i data center che forniscono servizi di **cloud computing**.
- Gli attuali **supercomputer e High Performance Computers (HPC)**, incluse macchine come l'IBM POWER5, l'HP Alphaserver o il Cray XT3.

