L'architettura **MISD** (acronimo di **Multiple Instruction, Single Data**, ovvero "Istruzioni Multiple, Singolo Dato") è la terza categoria della tassonomia di Flynn e rappresenta sicuramente il modello più insolito del gruppo.

![[Pasted image 20260303121957.png]]

Ecco come funziona nel dettaglio:

- **Multiplo Flusso di Istruzioni (Multiple Instruction):** A differenza dei modelli SISD e SIMD, in questo caso il sistema gestisce più flussi di istruzioni (o programmi) indipendenti. Ci sono diverse Unità di Controllo (CU) e ciascuna preleva le proprie istruzioni dalla memoria per configurare la propria Unità di Elaborazione (PU).
- **Singolo Flusso di Dati (Single Data):** Tutte queste unità di elaborazione, pur eseguendo istruzioni e calcoli completamente diversi, agiscono simultaneamente **sullo stesso identico flusso di dati**. Per fare un esempio pratico: è come avere due numeri (float) in ingresso e far calcolare contemporaneamente a una prima unità la loro somma, a una seconda il loro prodotto e a una terza la loro sottrazione.

**Caratteristiche e Comportamento:** La particolarità principale della classe MISD è che viene considerata un'architettura "anomala", definita e inserita nella tassonomia quasi esclusivamente per **completezza teorica**. Nell'uso quotidiano o nei computer che utilizziamo normalmente, macchine di questo tipo praticamente non esistono.

**Esempi storici e Applicazioni:**

- **Esempi storici:** Le implementazioni reali di questa architettura sono state rarissime e per lo più legate a progetti di ricerca sperimentali. Uno dei pochissimi esempi concreti citati in letteratura è il computer sperimentale **C.mmp della Carnegie-Mellon**, sviluppato nel 1971.
- **Casi d'uso ipotetici:** Sebbene rarissima a livello hardware, l'idea alla base del MISD trova alcune concezioni teoriche valide in scenari estremamente specializzati in cui lo stesso dato deve subire più analisi simultanee. Tra i possibili utilizzi troviamo:
    - L'applicazione contemporanea di molteplici filtri di frequenza diversi a un singolo flusso di segnale.
    - L'esecuzione parallela di molteplici algoritmi di crittografia che tentano simultaneamente di decifrare un singolo messaggio in codice.