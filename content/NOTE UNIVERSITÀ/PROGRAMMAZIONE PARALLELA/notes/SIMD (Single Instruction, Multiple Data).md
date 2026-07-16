L'architettura **SIMD** (acronimo di **Single Instruction, Multiple Data**, ovvero "Singola Istruzione, Dati Multipli") descrive una specifica tipologia di computer **parallelo**. È il modello che sta alla base di gran parte dell'accelerazione hardware moderna.

![[Pasted image 20260303121240.png]]

Ecco i dettagli del suo funzionamento:

- **Singolo Flusso di Istruzioni (Single Instruction):** L'Unità di Controllo (CU) carica dalla memoria **un'unica istruzione alla volta** in un dato ciclo di clock. La grande differenza rispetto al modello SISD è che la CU utilizza questa singola istruzione per configurare e istruire **più Unità di Elaborazione (PU) contemporaneamente**.
- **Multiplo Flusso di Dati (Multiple Data):** Tutte queste unità di calcolo eseguono contemporaneamente l'istruzione appena ricevuta, ma ciascuna opera su **elementi di dati (operandi) differenti**. Per fare un esempio: se l'istruzione è un'addizione tra due array matematici (x e y), la prima unità sommerà il primo elemento di x con il primo di y, la seconda unità sommerà i secondi elementi, la terza i terzi, e così via.

**Caratteristiche e Comportamento:**

- **Esecuzione Sincronizzata (Lockstep):** L'esecuzione è rigorosamente sincronizzata a livello di istruzione. Tutte le unità di processing eseguono la stessa istruzione simultaneamente; la macchina attende che tutte abbiano concluso l'operazione sui rispettivi dati prima di passare a caricare ed eseguire l'istruzione successiva del programma. L'esecuzione risulta quindi deterministica.
- **Dominio di applicazione:** Questo approccio non va bene per codici ricchi di diramazioni logiche (come i cicli condizionali asimmetrici), ma è **ideale per problemi altamente regolari**, dove la stessa operazione matematica deve essere ripetuta su enormi moli di dati strutturati, come avviene nell'elaborazione di immagini, grafica e matrici.

**Esempi storici e attuali:**

- Storicamente, i computer SIMD si dividevano in due varianti principali: i _Processor Arrays_ (come l'ILLIAC IV o il MasPar) e le _Vector Pipelines_ (come i celebri supercomputer della linea Cray, ad esempio il Cray X-MP e Y-MP).
- Oggi, i rappresentanti più famosi e diffusi di questa categoria sono le **moderne GPU (Graphics Processing Unit)**. Gran parte dei computer odierni e l'intero settore dell'Intelligenza Artificiale sfruttano massicciamente le unità di esecuzione SIMD per calcolare operazioni in parallelo.