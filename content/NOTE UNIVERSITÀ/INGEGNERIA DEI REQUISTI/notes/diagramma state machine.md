
I diagrammi delle macchine a stati catturano i comportamenti ammissibili dei componenti del sistema

Essi rappresentano la sequenza delle transizioni di stato per gli elementi controllati.

Comportamento di un’istanza di componente:
- Sequenza di transizioni di stato per gli elementi che controlla.
- Stato della Macchina a Stati: Insieme di situazioni in cui una variabile che caratterizza un elemento controllato ha sempre lo stesso valore. Ad esempio, lo stato “MeetingScheduled” ha sempre lo stesso valore per “Date” e “Location”.
- Stati Iniziali e Finali: Stati in cui l’elemento appare o scompare. Gli stati possono avere una certa durata. 
- Transizione di Stato della Macchina a Stati: 
	Causata da un evento associato. Se l’elemento è nello stato di origine e l’evento si verifica, allora passa allo stato di destinazione. Gli eventi sono fenomeni istantanei.

![[Pasted image 20250606135247.png]]
Le guardie (parentesi quadre) rappresentano controlli booleani per controllare il flusso di esecuzione

Un evento è una condizione sufficiente per transire da uno stato all'altro

![[Pasted image 20250606135620.png]]
![[Pasted image 20250606135630.png]]

