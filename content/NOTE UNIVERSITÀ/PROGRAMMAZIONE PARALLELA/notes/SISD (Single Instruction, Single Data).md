L'architettura **SISD** (**Single Instruction, Single Data**),descrive i computer di tipo **seriale (non parallelo)**, corrispondendo esattamente alla classica architettura di Von Neumann.

![[Pasted image 20260303115850.png]]

Ecco i dettagli del suo funzionamento:

- **Singolo Flusso di Istruzioni (Single Instruction):** In questo modello, l'Unità di Controllo (CU) preleva dalla Memoria Principale (MM) **una singola istruzione alla volta**. In un dato ciclo di clock, c'è un solo programma in esecuzione e la CPU agisce su un unico flusso di istruzioni.
- **Singolo Flusso di Dati (Single Data):** L'Unità di Elaborazione (PU) esegue l'istruzione ricevuta operando su un **singolo flusso di dati** come input per ogni ciclo di clock. L'unità di elaborazione interagisce con la memoria caricando i dati necessari per il calcolo (operazioni di _load_) e, una volta terminata l'operazione, salva il risultato sempre in memoria (operazioni di _store_).

**Caratteristiche e Comportamento:** Poiché le istruzioni passano rigorosamente in fila, una dopo l'altra, l'esecuzione del codice è completamente **sequenziale e deterministica**. Questo è il paradigma a cui i programmatori sono stati tradizionalmente abituati per decenni.

**Esempi storici e il suo "capolinea":** La classe SISD raggruppa la stragrande maggioranza della storia dell'informatica classica, in particolare i vecchi mainframe, i minicomputer e le workstation:

- Si parte dai primissimi calcolatori degli anni '40, come l'**UNIVAC1**, che veniva utilizzato durante la guerra per calcolare le traiettorie balistiche.
- Comprende macchine storiche come l'IBM 360, il PDP1, il CRAY1 e il CDC 7600.
- Il rappresentante finale di questa categoria nel mercato di massa è stato l'**Intel Pentium 4**. Il Pentium 4 è considerato l'ultimo vero processore _single-core_ e prettamente sequenziale; dopo di esso, l'industria ha compreso che non era più possibile aumentare le prestazioni affidandosi solo all'aumento della frequenza di clock del singolo processore. Da quel momento in poi, si è passati all'aggiunta di unità parallele (multi-core), abbandonando il puro modello SISD