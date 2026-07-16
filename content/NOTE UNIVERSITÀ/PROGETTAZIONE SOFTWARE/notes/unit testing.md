- **Scopo:** Testare singole unità (funzioni, classi, metodi) isolandole il più possibile dal resto del codice.
	![[Pasted image 20260118151356.png]]
	![[Pasted image 20260118151501.png]]
- **Caratteristiche:** Viene svolto dallo sviluppatore. Spesso si usano **Stub** e **Mock objects**, ovvero degli oggetti che simulano funzionalità o dipendenze non ancora implementate di altre classi, per mantenere l'isolamento. Per isolamento si intende anche evitare errori dalle altre unità. I mock devono offrire ovviamente la stessa interfaccia
- **Automazione:** È essenziale automatizzare questi test (Setup -> Chiamata -> Asserzione) per poterli rieseguire senza intervento manuale.![[Pasted image 20260118152033.png]]
- **Test Driven Development (TDD):** Un approccio agile dove i test e gli scenari vengono scritti _prima_ del codice. Il ciclo è: 
	Scrivi test -> Il test fallisce -> Implementi la funzionalità -> Il test passa.
	![[Pasted image 20260118153123.png]]
	i vantaggi del tdd sono:
	1. **Copertura del Codice (Code Coverage):** Garantisce che vi sia almeno un caso di test per ogni segmento di codice del sistema, poiché il codice viene scritto solo per passare un test esistente.
	
	2. **Test di Regressione (Regression Test):** È sempre possibile eseguire automaticamente tutti i casi di test; di conseguenza, le funzionalità esistenti vengono verificate ogni volta che si aggiunge una nuova funzionalità per assicurarsi che non siano stati introdotti errori.
	
	3. **Debugging Semplificato:** Poiché nel TDD si lavora su piccoli incrementi, se un test fallisce è immediatamente chiaro che il problema risiede nella singola funzionalità appena sviluppata o modificata, rendendo ovvia la localizzazione del difetto. I problemi vengono scoperti _durante_ lo sviluppo stesso del codice.
	
	4. **Documentazione del Sistema:** I test scritti fungono da documentazione viva che può essere letta per comprendere le caratteristiche e le funzionalità del sistema.
	
