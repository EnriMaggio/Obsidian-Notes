 #### Data: 05/02/2025 - 16:27

Ci devono essere almeno L valori sensibili differenti in ogni classe di equivalenza. Questa tecnica ha lo scopo di impedire agli attaccanti di dedurre l'appartenenza dei dati di un record ad una identità aiutandosi con dei dati di documenti esterni.

![[Pasted image 20250205170047.png]]

### Storico delle evoluzioni di l-diversity

- **Distinct l-diversity**: 
  Ogni classe di equivalenza deve avere almeno *l* valori sensibili ben rappresentati.
  ⚠️ Non previene attacchi di deduzione probabilistica perché alcuni valori sensibili possono essere molto più rappresentati di altri. ![[Pasted image 20250205170250.png]]
  
- **Entropy l-diversity**: 
  Non basta avere valori distinti, ma questi devono essere distribuiti in modo equilibrato. 
  Si utilizza la **entropia** per misurare la distribuzione dei valori sensibili, e questa deve risultare almeno $$log(l)$$![[Pasted image 20250205170350.png]]

La L-Diversity presenta ancora comunque problemi per quanto riguarda attacchi di inferenza probabilistica. Inoltre non considera la correlazione semantica tra i valori sensibili e non riesce a gestire bene situazioni in cui i valori sensibili sono estremamente sbilanciati

![[Pasted image 20250205171321.png]]
![[Pasted image 20250205171402.png]]
#### REFERENZE: https://www.youtube.com/watch?v=GNhb3PcmjmA