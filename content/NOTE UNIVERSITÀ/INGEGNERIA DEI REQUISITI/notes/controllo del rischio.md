in questa fase si ragiona sui rischi e si cerca di ridurli

L’obiettivo principale nella gestione dei rischi è ridurre l’esposizione ai rischi più critici attraverso l’implementazione di contromisure efficaci. Queste contromisure non solo mitigano i rischi esistenti ma possono anche portare all’ emergere di nuovi requisiti per affrontare condizioni o sfide non precedentemente identificate. 

L’adozione di tali misure richiede un’analisi accurata e una valutazione continua per assicurare che i rischi vengano gestiti in modo proattivo e che le soluzioni implementate migliorino effettivamente la robustezza del sistema o del processo.

delle contromisure immediate sono:
- elicitazione
- utilizzare contromisure effettive che si conoscono già
- usare tattiche di riduzione dei rischi


---
### tattiche di riduzione del rischio

- **Ridurre la probabilità del rischio**: aggiunta di requisiti che riducono significativamente la probabilità.
    
    - Esempio: “Segnali regolari per notificare il conducente”.
        
- **Evitare il rischio**: requisiti che impediscono che il rischio si verifichi.
    
    - Esempio: “Apertura porte solo tramite attuatori controllati da software”.
        
- **Ridurre la probabilità delle conseguenze**: requisiti che limitano la probabilità di effetti negativi.
    
    - Esempio: “Allarme se la porta si apre mentre il treno è in movimento”.
        
- **Evitare le conseguenze del rischio**: requisiti che eliminano completamente l’effetto negativo.
    
    - Esempio: “Nessuna collisione anche in caso di errori nella stima della velocità”.
        
- **Mitigare la severità delle conseguenze**: ridurre l’impatto delle conseguenze.
    
    - Esempio: “Passeggeri informati sui ritardi”.



---
### Confronto delle opzioni alternative

l processo di Ingegneria dei Requisiti solleva diverse opzioni alternative per soddisfare gli obiettivi di un sistema, risolvere i conflitti e ridurre i rischi. La selezione delle alternative preferite richiede una negoziazione basata su criteri ben definiti.

Per selezionare le alternative preferenziali, si concorda sui seguenti criteri:
-  Contributo ai requisiti non funzionali critici (sono quantitativi).
-  Contributo alla risoluzione di altri rischi.
-  Costo-efficacia, misurato attraverso il leverage di riduzione del rischio (ovvero il beneficio che ci portano rispetto al costo che dobbiamo pagare)

- Formula:
    
    RRLr,cm=EXPr−EXPr∣cmCostr,cmRRL_{r,cm} = \frac{EXP_r - EXP_{r|cm}}{Cost_{r,cm}}RRLr,cm​=Costr,cm​EXPr​−EXPr∣cm​​
    
    Dove:
    
    - EXPrEXP_rEXPr​: esposizione del rischio r.
        
    - EXPr∣cmEXP_{r|cm}EXPr∣cm​: esposizione residua dopo la contromisura cm.
        
    - Costr,cmCost_{r,cm}Costr,cm​: costo della contromisura.
        
- **Scegliere le contromisure con RRL più alto**.
    
- Possibilità di combinarle per RRL cumulativi.

---
### Documentazione rischi

La documentazione accurata dei rischi è fondamentale per supportare l’evoluzione del sistema e garantire che le contromisure siano adeguatamente pianificate e implementate. 

Per ogni rischio identificato è necessario registrare:

- Condizioni/eventi che lo attivano.
- Probabilità stimata.
- Cause e conseguenze potenziali.
- Probabilità e gravità di ogni conseguenza.
- Contromisure identificate + RRL.
- Contromisure selezionate.