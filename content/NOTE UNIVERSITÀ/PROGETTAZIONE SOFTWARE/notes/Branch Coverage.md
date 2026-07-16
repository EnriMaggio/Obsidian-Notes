 Questa copertura richiede che ogni ramo (vero/falso) delle decisioni (if, while, switch) sia percorso durante l'esecuzione almeno una volta dalla nostra batteria di test. È di fatto una copertura esaustiva. Verficare tutti i branch significa controllare:
 - ramo vero e falso di un if
 - ogni caso di uno switch case
 - cicli iterativi
![[Pasted image 20260122152933.png]]

Il problema avviene quando non ci sono espressioni atomiche nelle istruzioni condizionali, perchè richiede di testare una varia combinazione di essi, e non più due
