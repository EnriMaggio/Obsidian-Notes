**Statechart (o Harel Statechart, Diagramma a Stati UML):**

- **Cos'è:** Le Statechart (introdotte da David Harel) sono un'estensione dei diagrammi a stati tradizionali (FSM) che permettono di modellare comportamenti più complessi in modo più conciso e leggibile, evitando la "combinatorial explosion" (esplosione combinatoria) di stati che si verificherebbe con le FSM tradizionali per sistemi complessi. Sono la base per i diagrammi a stati nel linguaggio UML (Unified Modeling Language).
- **Come differisce dalla State Machine (nel contesto dell'ingegneria dei requisiti):**
    1. **Gerarchia (Stati Annidati):** Una delle differenze più significative. Le Statechart permettono di definire stati complessi che contengono a loro volta altri stati (sottostati). Questo riduce la complessità del diagramma e riflette meglio le gerarchie naturali del sistema. Ad esempio, uno stato "Acceso" di un telefono potrebbe contenere sottostati come "In Attesa", "In Chiamata", "In Modalità Aereo".
    2. **Ortogonalità/Concorrenza (Stati Paralleli):** Le Statechart consentono di modellare comportamenti concorrenti, dove diverse parti del sistema possono trovarsi in stati diversi simultaneamente e in modo indipendente. Questo è rappresentato da stati divisi in regioni ortogonali. Ad esempio, un'auto può essere "Accesa" (un aspetto) e contemporaneamente avere i "Fari Accesi" (un altro aspetto indipendente).
    3. **Comunicazione Broadcast:** Facilitano la modellazione di eventi che possono influenzare più stati o componenti contemporaneamente.
    4. **Storia (History States):** Permettono al sistema di "ricordare" l'ultimo sottostato attivo all'interno di uno stato composito quando ci si rientra.
    5. **Azioni (Entry/Exit Actions, Internal Transitions):** Consentono di specificare azioni che vengono eseguite all'ingresso di uno stato, all'uscita da uno stato o in risposta a un evento mentre si rimane nello stesso stato.

**In sintesi, nell'ingegneria dei requisiti:**

- Le **State Machine** sono adatte per modellare comportamenti relativamente semplici con un numero limitato di stati e transizioni dirette.
- Le **Statechart** sono preferite per sistemi complessi e reattivi, dove la gerarchia, la concorrenza e le azioni associate agli stati sono essenziali per catturare in modo chiaro e gestibile i requisiti dinamici. Offrono una rappresentazione più compatta e comprensibile, riducendo la necessità di un'esplosione esponenziale di stati e transizioni. Sono lo strumento standard in UML per la modellazione del comportamento dinamico.

![[Pasted image 20250606140343.png]]