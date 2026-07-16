- **Scopo:** Quando tutti i componenti sono a posto,  si integrano tutti componenti per realizzare il sistema e testare il sistema come un tutt'uno. Si testeranno non algoritmi, ma funzionalità che hanno senso per l'utente finale.
- **Focus:** Verificare le interazioni tra componenti e assicurarsi che il sistema soddisfi i requisiti (funzionali e non funzionali come performance e sicurezza).
- **Metodologia:** Spesso si basa sui "Use Cases" (casi d'uso) per identificare le interazioni e le sequenze di sistema da testare. I casi d'uso sono coerenti per testare il sistema, perchè di base essi testano ad alto livello funzionalità che verranno usate dall'utente finale. Rappresenta il contratto tra chi ha lavorato sui requisiti e chi ha lavorato sul sistema software. Un caso d'uso può essere implementato attraverso un sequence diagram![[Pasted image 20260118160631.png]]
- **Policies:** poiché è impossibile testare tutte le possibili esecuzioni di un sistema, è necessario stabilire delle **Testing Policies** (politiche di test) per definire quando l'attività di testing può essere considerata "adeguata" (conclusa). Alcuni esempi sono

	• **Copertura delle istruzioni:** Tutte le istruzioni presenti nel programma devono essere eseguite da almeno un test.
	
	• **Funzioni da menu:** Tutte le funzioni del sistema accessibili tramite menu devono essere testate.
	
	• **Combinazioni:** Devono essere testate le combinazioni di funzioni accessibili attraverso lo stesso menu.
	
	• **Input utente:** In tutti i punti in cui è previsto un input da parte dell'utente, le funzioni devono essere testate sia con input corretti che con input non corretti (errati).