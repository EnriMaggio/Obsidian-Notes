Per avere un’implementazione corretta e completa del software dobbiamo fare in modo che il software risolva un problema concreto del mondo reale. Dobbiamo quindi comprendere correttamente il mondo reale, ovvero come funziona, come dovrebbe funzionare, quali sono i vincoli che governano, capire il contesto in cui il software deve operare. Questo è il compito dell’ingegneria dei requisiti.

per requisito si intende cosa è necessario che il software fornisca, e anche la descrizione di quali problemi da risolvere nel contesto in cui sussistono questi problemi

ad esempio

- Problema: la gestione del freno a mano in un’automobile moderna potrebbe essere automatizzato. 
-  Contesto: se l’automobile è in movimento, se si sta frenando, se è intenzione del guidatore fermarsi, se il guidatore ha premuto il pedale del freno, 

Per descrivere bene un requisito devo modellare per bene tutto quello che sta intorno

- **Mondo**
	fa a riferimento a tutte le parti problematiche del mondo reale.
	Abbiamo a che fare con elementi molto complessi che contengono di fatto elementi umani (lo staff, l’utente, il cliente, . . . ), elementi fisici (dispositivi, software legacy, la natura, . . . ) e dovrà quindi adattarsi alla situazione esistente
- **Macchine**
	Parliamo quindi di tutto ciò che dovrà essere implementato e/o acquistato, come ad esempio database, server, client, . . . e i componenti hardware e software che dovranno essere implementati, il tutto per risolvere i problemi

L’ingegneria dei requisiti non si limita solamente al mondo delle macchine, ma tiene in considerazione anche gli effetti che il software ha sul mondo reale, che dovrà modellare.

![[Pasted image 20250604110815.png]]
questa immagine descrive come i domini dei mondi e delle macchine hanno dei propri fenomeni, alcuni sono condivisi in entrambi i domini. L'ingegneria dei requisiti descrive l'intersezione dei due domini e l'universo del mondo, non sono quindi considerati aspetti tecnici e implementativi del dominio macchina


---
### Sistema

Il sistema è un insieme di componenti che interagiscono che strutturano il mondo e ne esistono due

1. **sistema as-is** 
	 si tratta del sistema prima che il software venga implementato. Questo sistema è composto solamente dal mondo.
2. **sistema to-be**
	si tratta del sistema come dovrebbe essere quando il software opererà. Questo sistema è composto dall'unione del mondo e delle macchine.

![[Pasted image 20250604112138.png]]

L'ingegneria dei requisti, di fronte a questi due sistemi, è una serie di attività coordinate che permettono di esplorare, valutare, documentare, consolidare, rivedere e adattare quelli che sono gli obiettivi, le capacità, i vincoli e le assunzioni in un sistema software. Basato sui problemi del sistema as-is e le opportunità date dalle nuove tecnologie.


---
### Requisiti di sistema vs requisiti software

- **requisiti di sistema**
	sono i servizi e le frasi prescrittive che il futuro sistem to be soddisfacirà e sono relative in termini di fenomeni nell'ambiente ad esempio
	"il freno mano deve essere rilasciato quando il guidatore vuole partire"
- __requisito software__
	sono frasi prescrittive che descrivono come il software nel system to be dovrà fare in autonomo e sono formulati in termini di fenomeni che sono condivisi tra il software e ambiente
	ad esempio
	 ![[Pasted image 20250604113555.png]] 

---
### Scope dell'ingegneria dei requisiti

![[Pasted image 20250604113806.png]]