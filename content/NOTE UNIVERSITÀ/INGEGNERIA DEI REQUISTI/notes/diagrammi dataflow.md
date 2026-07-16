ci descrivono quali sono i flussi dei dati, in particolare ci specifica come i dati vengono generati durante l'esecuzione del nostro sistema

è composto da 
- **Operazione:** attività di trasformazione dei dati.
- **Link di input e output:** flussi di dati.
    - Un'operazione necessita di dati che _fluiranno in entrata_ per produrre dati che _fluiranno in uscita_ (= flusso di controllo!).
- **Regola di trasformazione dei dati da specificare...**
    - ... in annotazione (LN strutturato - Linguaggio Naturale strutturato)
    - ... oppure in un altro DFD (Data Flow Diagram - Diagramma di Flusso Dati) (raffinamento dell'operazione, cfr. SADT).
- **Componenti del sistema, repository di dati:** origini e terminazioni del flusso.
- **Regole di consistenza/completezza:** verificabili tramite strumenti, cfr. SADT.


![[Pasted image 20250606132857.png]]

Questo diagramma si presta in maniera più diretta per parlare con gli stakeholder, in quanto presenta una semantica più intuitiva, anche se risulta meno espressivo