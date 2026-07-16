- **Scopo:** Testare come i moduli interagiscono tra loro quando vengono combinati.
- **Focus:** L'attenzione è sulle **interfacce** tra i componenti, non sulla funzionalità interna delle singole unità (che si assume già testata). Si va a controllare l'interazione dei dati tra i componenti. I componenti a sua volta fanno delle assunzioni sul come si aspettano che le altre classi vengono chiamate, e con quali valori di ritorno.

vengono classificati quattro tipi principali di interfacce attraverso le quali i componenti software interagiscono:

1. **Interfacce a Parametri (Parameter interfaces):** I dati vengono passati da un metodo o una procedura a un altro direttamente tramite parametri.
2. **Interfacce a Memoria Condivisa (Shared memory interfaces):** Un blocco di memoria viene condiviso tra diverse procedure o funzioni; questa tipologia è citata come comune nei sistemi integrati che gestiscono sensori (sistemi embedded).
3. **Interfacce Procedurali (Procedural interfaces):** Un sottosistema incapsula un set di procedure (o metodi) che vengono esposte per essere chiamate da altri sottosistemi.
4. **Interfacce a Scambio di Messaggi (Message passing interfaces):** I sottosistemi richiedono servizi ad altri sottosistemi inviando messaggi; questo meccanismo è tipico dei sistemi distribuiti o client-server.

- **Errori comuni rilevati:**
    - Uso scorretto dell'interfaccia (es. ordine parametri errato, passare dati ai parametri con tipo sbagliato).
    - Incomprensioni sul comportamento atteso del componente chiamato, perchè vari moduli assumono quello che si aspettano.
    - Errori di tempistica (timing errors) in sistemi real-time o a memoria condivisa.

le linee guida per scrivere test per interfacce sono:

**1. Testare i limiti dei parametri** Quando si testano interfacce procedurali o a parametri, è fondamentale chiamare le procedure utilizzando valori che si trovano agli **estremi dei loro intervalli** (ranges). Questo aiuta a verificare come il componente gestisce i casi limite.

**2. Testare i puntatori Null** Se l'interfaccia prevede l'uso di puntatori, bisogna includere test specifici che passano **puntatori nulli**. Questo è un controllo essenziale per evitare crash imprevisti dovuti alla mancata gestione di riferimenti vuoti.

**3. Forzare il fallimento (Failure Testing)** Non bisogna testare solo il "percorso felice" (successo). Le linee guida suggeriscono di progettare test che causino intenzionalmente il **fallimento del componente**, per vedere se lanciano l'eccezione corretta, in modo che l'esecuzione scorretta sia controllata. 

**4. Stress Testing per Scambio di Messaggi** Nei sistemi che utilizzano interfacce a _Message Passing_ (comuni in architetture distribuite o client-server), si raccomanda l'uso dello **stress testing**

• _Obiettivo:_ Questo approccio serve a rivelare **errori di timing**, come il tentativo di leggere un messaggio prima che sia pronto o problemi di sincronizzazione tra componenti che operano a velocità diverse.

**5. Variare l'ordine di attivazione nella Memoria Condivisa** Nei sistemi con interfacce a _Shared Memory_ (tipici dei sistemi embedded o real-time), una linea guida critica è **variare l'ordine in cui i componenti vengono attivati**.

• _Obiettivo:_ Questo aiuta a rivelare assunzioni implicite (e spesso errate) fatte dagli sviluppatori sulla sequenza di produzione e consumo dei dati (es. produttore/consumatore).