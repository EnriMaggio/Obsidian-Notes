è una versione customizzata per l'ingegneria dei requisiti. Quello che fa in sostanza è dichiarare gli oggetti concecttuali e le loro varie relazioni.

Il diagramma è composto da:

- **Entità:** classe di istanze di concetti...
    - aventi identità distinte
    - che condividono caratteristiche comuni (attributi, relazioni)
    - es. Riunione, Partecipante
- **Relazione N-aria:** 
	caratteristica che collega concettualmente N entità, ciascuna con un ruolo distintivo (N ≥ 2)
    - **Molteplicità**, su un lato: numero min & max di istanze di entità, su questo lato, collegabili contemporaneamente a una singola tupla di istanze di entità sugli altri lati
    - es. Invito che collega Partecipante e Riunione
- **Attributo:** caratteristica intrinseca a un'entità o a una relazione
    - ha un intervallo di valori
    - es. Data della Riunione


![[Pasted image 20250606131138.png]]
Da notare che le entità non sono componenti software, ma sono per modellare le informazioni e i concetti del dominio corrente, quindi sono utilizzati per descrivere il problema 

Gli uml nell'ingegneria dei requisiti fa un uso estensivo delle annotazioni o commenti (statement in linguaggio naturale) 