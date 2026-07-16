
È un modello gerarchico fondamentale per organizzare sistemi complessi. Questa architettura prevede la presenza e l'organizzazione delle funzionalità in strati separati e distinti.

Questo approccio supporta lo sviluppo incrementale del software e ne favorisce la **portabilità**, ovvero si può sostituire uno strato con un altro che presenta una implementazione diversa, mantendo ovviamente le stesse interfacce delle funzionalità

![[Pasted image 20260117145834.png]]
La caratteristica di questa architettura è la comunicazione tra i vari layer, ogni layer fornisce delle funzionalità al layer successivo e utilizza dei servizi del layer precedente

Questa architettura viene utilzzata in tre contesti specifici in cui questo pattern è particolarmente indicato:

• **Estensione di sistemi:** Quando si costruiscono nuove funzionalità sopra a sistemi esistenti.

• **Sviluppo distribuito:** Quando il lavoro è suddiviso tra più team, ognuno dei quali si assume la responsabilità di un singolo strato di funzionalità. Ovviamente prima bisogna accordare lo scambio dei messaggi tra i vari strati

• **Requisiti di sicurezza:** Quando è necessario implementare una sicurezza multilivello.

Esempi classici includono il modello **ISO OSI** per le reti e l'architettura del sistema operativo **Android**

![[Pasted image 20260117150743.png]]

Vantaggi:
• **Sostituibilità:** 
	È possibile sostituire un intero strato (ad esempio, cambiare il database o l'interfaccia utente) senza influenzare il resto del sistema, a condizione che l'interfaccia pubblica dello strato rimanga invariata.
• **Affidabilità (Dependability):** 
	Permette di inserire controlli ridondanti (come l'autenticazione) in ogni singolo strato, aumentando la robustezza complessiva del sistema (verifica in livelli diversi).

Svantaggi e Criticità:
• **Separazione imperfetta:** 
	Nella pratica, mantenere una separazione pulita tra i livelli è spesso difficile. Talvolta, uno strato di alto livello potrebbe aver bisogno di interagire direttamente con strati di basso livello (saltando quello intermedio), rompendo la purezza del modello.
• **Prestazioni:** 
	Le performance possono degradare perché ogni richiesta di servizio deve attraversare molteplici livelli di interpretazione ed elaborazione prima di essere completata.