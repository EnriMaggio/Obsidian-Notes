Il cuore di questo pattern è la presenza di un **database centrale** (il repository) che detiene tutti i dati condivisi del sistema. La caratteristica distintiva rispetto ad altri approcci è il modello di comunicazione: **non esiste comunicazione diretta tra i sottosistemi** periferici. Questa architettura è il modello di riferimento per i sistemi "data-driven" (guidati dai dati).

![[Pasted image 20260117152601.png]]
- I sottosistemi interagiscono esclusivamente con il repository.
- Un componente produce dati e li salva nel repository; un altro componente li legge e li utilizza.
- L'attivazione di un tool o di un'azione è spesso innescata proprio dall'inclusione di nuovi dati nel repository.

Vari esempi di applicazioni che utilizzano l'architettura repository sono:

![[Pasted image 20260117152801.png]]
![[Pasted image 20260117152817.png]]
![[Pasted image 20260117152845.png]]

Questa architettura viene usata quando
- si gestiscono **grandi volumi di informazioni** che devono essere conservati per lungo tempo.
- In sistemi **data-driven**, dove le operazioni sono attivate dalla presenza o dalla modifica dei dati piuttosto che da chiamate esplicite tra componenti.

Vantaggi:

- **Indipendenza dei componenti:**
	I sottosistemi non hanno bisogno di sapere dell'esistenza degli altri componenti per funzionare. I componenti sono autonomi e possono evolvere in modo indipendente

- **Gestione coerente:**
	Poiché i dati sono in un unico posto, è facile gestirli in modo uniforme (ad esempio, effettuando backup centralizzati).

- **Propagazione delle modifiche:**
	Una modifica effettuata da un componente viene immediatamente resa disponibile a tutti gli altri senza bisogno di complessi meccanismi di notifica peer-to-peer.


Svantaggi:

- **Single Point of Failure (Punto singolo di guasto):**
	Se il repository centrale si guasta o diventa inaccessibile, l'intero sistema smette di funzionare.

- **Inefficienza:**
	Costringere tutte le comunicazioni a passare attraverso il repository può creare colli di bottiglia e rallentare il sistema rispetto alla comunicazione diretta.

- **Difficoltà di distribuzione:**
	Distribuire un repository centrale su più computer mantenendo la coerenza può essere tecnicamente complesso.