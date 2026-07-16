Questa sezione riguarda l'assegnamento delle responsabilità agli agenti che hanno il compito di soddisfare un goal a loro assegnato

Non si parla solo di responsabilità, ma anche di capacità, ovvero quali sono gli agenti che sono in grado di raggiungere i goal, chi ha interesse a raggiungerli e quelli a cui verrà assegnata la responsabilità del raggiungimento del goal.

- **Usi multipli**
    - mostrare la distribuzione delle responsabilità all'interno del sistema
    - analisi del carico
    - ambito e configurazione del sistema, confine software/ambiente
    - euristiche per l'assegnazione delle responsabilità
    - analisi delle vulnerabilità
    - input per la progettazione architetturale

un agente può essere dell'ambiente (persone, dispositivi) o del sistema to-be


---
### caratterizzazione agenti di sistema

- **Def:** condizione per un individuo per essere attualmente istanza di questo agente
- **Attributes/associations, Dom Invariants:** nell'object model
- **Category:** agente software o environment 
- **Capabilities:** quali oggetti e cose l'agente può monitorare e controllare
    - monitoring/control links to object model, cf next slides
- **Responsibility:** links to goal model
- **Performance:** azioni che l'agente può intraprendere
- **Dependency** links to other agents for goal satisfaction
- **Wishes** (for responsibility assignment heuristics)
- **Knowledge and beliefs** (for obstacle analysis, security analysis)


---
### Capacità agenti

Gli agenti hanno abilità di osservare ed avere visibilità su un oggetto, ovvero monitorare. Ed anche esercitare un controllo su un certo oggetto

![[Pasted image 20250612102728.png]]

Di fatto, quello che gli agenti possono monitorare non sono solo dati, ma ogni tipologia di oggetto, ad esempio un agente potrebbe monitorare un campo di un oggetto, la presenza di associazioni tra oggetti, ecc.

![[Pasted image 20250612102837.png]]

Una cosa importante da evitare è che non ci possono essere due agenti che controllano la stessa variabile


---
### Responsabilità agenti

gli agenti sono responsabili per il raggiungimento dei goal, e viene rappresentato con un responsibility link
![[Pasted image 20250612103205.png]]

Quando vengono assegnati delle responsabilità bisogna accertarsi che l'agente ha tutte le capabilities che gli permetto di raggiungere il goal (nell'esempio di prima il traincontroller deve avere per forza in grado di leggere il measureSpeed noto)

Un goal potrebbe essere non realizzabile per l’agente quando delle variabili importanti non possono essere monitorate o controllate dall’agente stesso. Se ci sono variabili di stato che vengono valutate in stati futuri, quando il goal esprime delle condizioni istantanee, allora il goal non è realizzabile. Un’altra condizione si verifica quando il goal non è soddisfacibile sotto determinate condizioni, ovvero il goal non è realizzabile in alcune situazioni.

Ci saranno problemi con gli achieve goal (se mi trovo in un certo stato, posso arrivare ad un altro stato) perchè può portare a procastinazione prolungata in caso ci condizione target continuamente posticipata

![[Pasted image 20250612103701.png]]
![[Pasted image 20250612104145.png]]


---
### Operazioni agenti

Gli agenti per esercitare la loro responsabilità, intrapprendeno delle azioni chiamate operazioni e vengono rappresentati con le elissi.

Le operazioni sono le cose che l'agente può fare per raggiungere il goal

![[Pasted image 20250612104637.png]]

Si utilizzano i performance link per collegare le operazioni all'agente


---
### Desideri agenti

sono utili anche modellarre i *whishes* degli agenti, ovvero le cose e gli obiettivi che un utente vorrebbe raggiungere. Questo ci aiuta a scegliere adeguamente e in modo efficace, l'agente per un certo goal rispetto ad altri

![[Pasted image 20250612104941.png]]


---
### Conoscenza e credenze degli agenti

E possibile modellare sia la conoscenza che le credenze degli agenti rispetto una memoria locale che l’agente possiede rispetto all’ambiente reale.

-  Un fatto F  è creduto dall’agente se F  è nella memoria locale dell’agente (perchè l'ha visto). 
- Un fatto F è conosciuto dall’agente se F è nella memoria locale dell’agente e F è vero, proprietà posseduta dall’ambiente o dal sistema.

Questo ci dice quello che un oggetto sa o non sa. Tale considerazione  è importante perchè ci permette di fare delle considerazioni sulla sicurezza.

---
### Dipendenza agenti 

sappiamo che ci potrebbe essere una relazione di dipendenza tra goal, quindi un agente prima di soddisfare il suo goal, deve aspettare il raggiungimento di alri goal responsabilizzati da altri agenti. Transitivamente un agente può dipendere da altri agenti

![[Pasted image 20250612110259.png]]

Le dipendenze sono direzionali e possono propagarsi a catena

![[Pasted image 20250612110758.png]]

In sistemi critici è opportuno non avere catene troppo lunghe

nel pattern del milestone c'è una dipendenza implicati tra due agenti

![[Pasted image 20250612111407.png]]



---
### Agent diagram

![[Pasted image 20250612112420.png]]

![[Pasted image 20250612111526.png]]

L'assegnamento delle responsabilità può essere alternativo, con un OR-assignment
![[Pasted image 20250612112253.png]]


---
### Context Diagram

È una vista che rappresenta solo gli agenti con dei link e abbiamo dei link fra un agente e l'altro quando un agente controlla o monitora delle grandezze da un altro agente. Controlla in sostanza le dipendenze di controllo e di monitoraggio tra i vari agenti

![[Pasted image 20250612112913.png]]
![[Pasted image 20250612112906.png]]
Ci permette di capire il canale di comunicazioni tra i diversi agenti di sistema, capire se esiston agenti isolati e non


---
### Dependency diagram

Il dependency diagram è una vista che rappresenta le dipendenze tra agenti.

![[Pasted image 20250612113515.png]]

Ci può aiutare a capire come i fallimenti si propagano nei goal e quali agenti potrebbero fallire


---
### Raffinamento degli agenti

Gli agenti possono essere raffinati in sottoagenti, come per i goal. Un agente più astratto viene scomposto, raffinato in più agenti, ogni sottoagente può avere un goal da raggiungere

![[Pasted image 20250612114016.png]]

Il raffinamento degli agenti:

- Supporta il perfezionamento incrementale delle responsabilità:
    - obiettivo a grana grossa assegnato ad un agente a grana grossa, poi sotto-obiettivi assegnati ad agenti a grana più fine
- L'agente a grana grossa può essere
    - agente ambientale ad esempio. dipartimento organizzativo -> unità -> operatori
    - ibrido: agente ambientale + software-to-be
    - per gli agenti software-to-be: rimandato alla progettazione architetturale

![[Pasted image 20250612114216.png]]


---
### Euristiche per modellare diagramma degli agenti

- **Identificazione degli agenti:** quando si legge la definizione di un goal, implicitamente nella definizione c'è il concetto di variabile,attributo controllata o monitorata. Bisogna chiedersi chi è in grado di modificare e leggere lo stato del sistema
- Quando leggiamo le **definizioni** possiamo vedere le azioni degli agenti.
- Quando assegniamo una responsabilità ad un agente umano bisogna valutare anche i **desideri** dell'utente (i goal di sicurezza informatica devono essere assegnati a persone che hanno a cuore la sicurezza del sistema, quindi in contrasto con il desiderio dell'utente finale).
- Non confondere agenti a livello di prodotto con gli stakeholder a livello di processo (durante l'elicitazione dei requisit). Gli agenti sono dei **ruoli**, mentre gli stakeholder sono delle persone che intervisto, di fatto la stessa persona potrebbe avere ruoli diversi ed essere modellato in agenti diversi.
- **Assegnare responsabilità a componenti software:** per raggiungere un livello di automazione maggiore (dipende e va valutato in base ai desideri).
- **Raffinare gli agenti in linea con i goal:** in modo da raggiungere una granularità tale da poter assegnare responsabilità in modo chiaro.
- Tener conto delle catene di dipendenze nell'assegnamento delle responsabilità


---
### Derivare context diagram dai goals

![[Pasted image 20250612115636.png]]