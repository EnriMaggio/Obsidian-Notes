#### Data: 08/10/2024 - 09:59

#### Tags: [[Teorema di Rice]]

L'analisi si fa in due momenti precisi nel ciclo di vita di un programma:
1. ==**STATICA**==
	si fa questa analisi senza l'esecuzione del programma (prima dell'esecuzione), quindi si estraggono informazioni sul codice sorgente. Deve essere un'analisi singola, che si fa una volta e può essere meno efficiente per garantire precisione (visto che l'analisi in questo caso avviene in modo indipendente dall'esecuzione del programma). Viene detto analisi white-box perchè va effettivamente a guardare tutto il codice
2. ==**DINAMICA**==
	si fa questa analisi sull'esecuzione del programma, quindi verifica che l'esecuzione singola (runtime) rispetti le proprietà semantiche. In generale è più facile da progettare e deve cercare di non impattare la performance del programma in termini di tempo e pesantezza. Viene detta analisi black-box perchè studia il legame tra input e output
