#### Data: 08/10/2024 - 10:38
#### Stato: #Done
#### Tags: 

Il **teorema di Church-Turing**, o più precisamente la **tesi di Church-Turing**, non è un teorema in senso stretto ma una proposta che riguarda il concetto di calcolabilità. Essa afferma che qualsiasi problema che può essere risolto meccanicamente, ossia tramite un algoritmo, può essere risolto da una macchina di Turing. Quindi, le macchine di Turing possono rappresentare formalmente il concetto di "calcolabilità" o "computabilità" in senso generale.

Tuttavia, ciò che è strettamente legato ai **problemi non decidibili** è l'**indecidibilità**, un concetto che si basa sulla teoria delle macchine di Turing. Questa teoria ci permette di identificare una classe di problemi che **non possono essere risolti da alcun algoritmo**.

### Teorema di Church-Turing e Indecidibilità

#### 1. **Tesio di Church-Turing (informale)**:

_"Qualsiasi funzione calcolabile in modo meccanico può essere calcolata da una macchina di Turing."_  
Questo significa che se esiste un metodo algoritmico per risolvere un problema, allora una macchina di Turing può risolverlo.

### 2. **Problemi decidibili vs. non decidibili**:

- Un **problema decidibile** è un problema per cui esiste un algoritmo che può risolverlo in un tempo finito per ogni possibile input. In altre parole, una macchina di Turing può determinare la risposta "sì" o "no" per ogni possibile input del problema.
- Un **problema non decidibile** è un problema per cui **non esiste un algoritmo** che possa risolverlo per tutti i casi. Anche se possiamo risolvere il problema per alcuni input, non possiamo risolverlo in modo generale per tutti gli input.

Un esempio classico di problema non decidibile è il **problema della terminazione** (Halting Problem), che è stato dimostrato indecidibile da Alan Turing nel 1936.

### 3. **Problema della terminazione (Halting Problem)**:

Il **problema della terminazione** chiede: dato un programma e un input, esiste un algoritmo che possa determinare se il programma terminerà (ovvero si fermerà) o andrà avanti all'infinito?

Turing dimostrò che non esiste un algoritmo generale in grado di risolvere questo problema per ogni possibile programma. In altre parole, non è possibile costruire una macchina di Turing che, dato un programma qualsiasi, possa sempre decidere se quel programma si fermerà o continuerà a funzionare indefinitamente.

La dimostrazione di Turing per l'indecidibilità del problema della terminazione si basa su un ragionamento per assurdo:

1. Supponiamo che esista una macchina HHH che possa decidere se un programma PPP su un input III terminerà o meno.
2. Costruiamo un nuovo programma P′P'P′ che utilizza HHH come sottoprogramma. Il programma P′P'P′ si comporta in modo paradossale, facendo esattamente il contrario di quello che HHH predice: se HHH dice che PPP termina, P′P'P′ continua indefinitamente, e se HHH dice che PPP non termina, allora P′P'P′ termina.
3. Questo porta a una contraddizione, dimostrando che la nostra assunzione iniziale (che esista una macchina HHH) è falsa. Quindi, il problema della terminazione è indecidibile.

### 4. **Problemi non decidibili correlati**:

Il problema della terminazione è solo uno dei molti problemi non decidibili. Grazie al teorema di Church-Turing, sappiamo che esistono molte altre classi di problemi che non possono essere risolti algoritmicamente, tra cui:

- **Problema dell'arresto per macchine di Turing**: Dato un programma (una macchina di Turing) e un input, determinare se la macchina di Turing terminerà su quell'input è indecidibile.
- **Problema della correttezza funzionale**: Stabilire se due programmi implementano la stessa funzione (ovvero, se per tutti gli input danno lo stesso output) è un problema indecidibile.
- **Problema dell'uguaglianza dei linguaggi**: Stabilire se due macchine di Turing riconoscono lo stesso linguaggio è indecidibile.
- **Problema dell'arresto per grammatiche libere dal contesto**: Determinare se una grammatica libera dal contesto genera una stringa vuota è anch'esso un problema indecidibile.

### 5. **Implicazioni del Teorema di Church-Turing per l'indecidibilità**:

Il teorema di Church-Turing, unito alla dimostrazione dell'indecidibilità del problema della terminazione, ci dice che ci sono limiti intrinseci a ciò che può essere calcolato da una macchina di Turing, e quindi da qualsiasi computer.

- **Non esistono algoritmi generali per risolvere problemi non decidibili**. Ad esempio, non possiamo avere un algoritmo che risolva in generale se un qualsiasi programma termina o meno.
- **Altri problemi indecidibili possono essere ridotti a problemi indecidibili noti**, come il problema della terminazione. Questo metodo di riduzione ci permette di dimostrare l'indecidibilità di nuovi problemi dimostrando che, se potessimo risolvere il nuovo problema, potremmo risolvere anche un problema già noto come indecidibile.