Questo pattern è fondamentale per la gestione dell'interazione, specialmente nei sistemi web e nelle app mobile (come Android). Separa il sistema in tre componenti logici, che hanno una responsabilità propria:

![[Pasted image 20260117120516.png]]

• **Model:** Gestisce lo stato e i dati del sistema attraverso un db. (logica del dato)
• **View:** Responsabile della resa grafica (UI) per mostrare i dati del modello.
• **Controller:** Gestisce gli eventi e l'input utente nella gui ed eventualmente apportare modifiche al model. (logica del business)

![[Pasted image 20260117120538.png]]
**Contesto di utilizzo:** È ideale quando ci sono molteplici modi di visualizzare e interagire con gli stessi dati o quando i requisiti futuri di presentazione sono sconosciuti. Questo perchè la rappresentazione dei dati è separata dalla loro visualizzazione
**Trade-off:** Il vantaggio principale è che i dati possono cambiare indipendentemente dalla loro rappresentazione (e viceversa). Lo svantaggio è che introduce una complessità di codice aggiuntiva che potrebbe essere eccessiva per modelli di dati semplici.

**Vantaggi:**
	• **Indipendenza tra dati e vista:** Permette ai dati di cambiare indipendentemente dalla loro rappresentazione e viceversa.
	• **Viste multiple:** Supporta la presentazione degli stessi dati in modi diversi.
	• **Sincronizzazione:** Le modifiche effettuate in una rappresentazione vengono mostrate in tutte le altre rappresentazioni.

**Svantaggi:**
	• **Complessità aggiuntiva:** Introduce una complessità di codice ("code complexity") supplementare che può risultare non necessaria se il modello dei dati e le interazioni sono semplici.