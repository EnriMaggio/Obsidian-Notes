#### Data: 07/10/2024 - 18:37

#### Tags:[[Teorema di Rice]]

Che cosa dobbiamo analizzare in fin dei conti?
1. che ==**programmi?**==
2. che ==**proprietà?**==
in funzione di queste risposte cambieremo lo strumento con cui utilizzare per fare l'analisi
### Programmi
- Domain-specific-analysis:
	analisi sono costruite per mirare/analizzare specifiche famiglie di programmi. Questo approccio funziona se applichiamo a programmi che fanno parte di una famiglia di programmi, perchè risulterà efficiente in quanto questa famiglia condividerà un particolare insieme di caratteristiche. Ovviamente questa analisi sarà poco esportabile per proprietà più complesse o che hanno bisogno di profondità, criticità importanti
- Non Domain-specific-analysis:
	sono analisi con un obiettivo più generico, guarda aspetti più generali, quindi non riguarda uno specifico linguaggio/programma
L'analisi può essere fatta a:
- livello di programma (codice sorgente)
- livello di modello
### Proprietà
ci sono 3 macroclassi di proprietà
1. ==**safety**==
	esclude specifici comportamenti non voluti in tempo finito, ovvero che niente di _"cattivo"_ può avvenire
2. ==**liveness**==
	prima o poi qualcosa di buono succederà, nel senso sancisce che il programma non esibirà mai comportamenti osservabili all'infinito. Non eseguirò niente di negativo all'infinito e quindi garantisce il verificarsi di comportamenti (attesi)
3. ==**information-flow**==
	fa più o meno le stesse cose della proprietà di safety ma ha bisogno necessariamente di più esecuzioni dello stesso programma a fronte di input 