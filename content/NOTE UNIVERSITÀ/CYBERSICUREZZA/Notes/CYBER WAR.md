#### Data: 04/11/2024 - 14:11

#### CyberWar su un sistema critico

Una CyberWar é un attacco informatico vasto, premeditato e studiato che vanno a colpire strutture critiche di un governo che sono necessarie ad esso per il funzionamento giornaliero di servizi importanti come elettrecità ecc. ecc. Inoltre possono essere target strutture che una volta compromesse potrebbero essere un potenziale pericolo per il popolo

![[Pasted image 20241104142651.png]]

L'obiettivo è quello di recare un danno molto grave agli stati e persino provocare perdite di vite umane

Questi attacchi sono svolti da gruppi di hacker sostenuti dallo stato o organizzazioni terroristiche
#### Cosa significa critico

Per critico intendiamo quando una risorsa(asset) persa o compromessa che può portare a
- un impatto significante sulla vita di una nazione per quanto riguarda la sua sicurezza o il funzionamento
- impatto dannoso sulla disponibilità, integrità e consegna di servizi essenziali

#### ICS

Molti delle strutture critiche sono controllate e gestionate dal ==**Industrial control Systems**==, ovvero l'integrazione dei strumenti e sistemi HW e SW con connettività di rete per sostenere le infrastrutture critiche

Gli ICS hanno il compito di

- garantire i processi industriali
- salvaguardare i processi critici
- controllo dello stato della struttura

Quando si parla di ICS bisogna distinguere tra IT e OT

- IT riguarda la tecnologia dell'informazioni
- OT riguarda la tecnologia operativa

Fanno parte dell’OT tutti i sistemi hardware e software che **monitorano e controllano** i dispositivi fisici sul campo. Le funzioni di Operational Technology variano a seconda del settore, come ad esempio i sensori che misurano la temperatura negli ambienti industriali.

Mentre l'IT gestisce la trasmissione dei dati generati dai sistemi OT, in modo che possono essere trasmessi a centri operativi dove le persone possono analizzare e tenere sotto controllo il processo industriale e prendere decisioni immediate in caso di problemi

La fusione di queste due componenti porta lo svantaggio della sicurezza (colpa dell'IT)

#### Componenti di un ICS

![[Pasted image 20241104144910.png]]

#### SCADA (SuperVisory Control And Data Acquisition)

E un componente della ICS che fa da controllo di supervisione e acquisizione dati. Questo componente è gestito da un centro operativo distante (da remoto )

Ogni sistema SCADA, nella sua generalità, si inserisce all’interno di una architettura che prevede:

- Uno o più computer interconnessi fra loro ai quali sono affidate le funzioni di supervisione e, in particolare, di interfaccia uomo-macchina
- Una serie di unità periferiche (RTU, Moduli di i/u o PLC) che si interfacciano direttamente con il processo (macchinari, impianto, etc.) tramite sensori e attuatori
- Una rete di comunicazione, caratterizzata da una molteplicità di mezzi trasmissivi e di protocolli di comunicazione, in grado di assicurare il corretto scambio di informazioni fra computer di supervisione e unità periferiche

![[Pasted image 20241104145957.png]]

#### Componenti di un ICS a rischio

![[Pasted image 20241104150112.png]]
#### Cyber War

E un'attacco cibernetico massivo verso un'infrastruttura di un governo nemico

![[Pasted image 20241104150842.png]]

#### Tipi di attacchi CyberWarfare

- ##### Spionaggio
	Si riferisce al monitoraggio di altri paesi per rubare segreti. Nella guerra informatica, questo può comportare l’uso di botnet, una rete di computer controllata e composta da dispositivi infettati da malware specializzato, detti bot, o attacchi di spear phishing, una truffa tramite comunicazioni elettroniche o e-mail indirizzata a una persona, un’organizzazione o un’azienda specifica per compromettere i sistemi informatici sensibili prima di esfiltrare informazioni sensibili.	
- ##### Malware e RansomWare
	Per cifrare o peggio fare il wipe delle informazioni del target
- ##### Wipers
	Unico scopo di cancellare i dati 
- ##### Sabotaggio
	Compromettere le infrastrutture per un periodo limitato di tempo
- ##### Attacchi DDos
	impediscono agli utenti legittimi di accedere a un sito web inondandolo di richieste false e costringendo il sito web a gestire queste richieste.
- ##### Attacchi alla rete elettrica
	Attaccare la rete elettrica permette agli aggressori di disabilitare i sistemi critici, interrompere le infrastrutture e potenzialmente provocare danni fisici. Gli attacchi alla rete elettrica possono anche interrompere le comunicazioni e rendere inutilizzabili servizi come messaggi di testo e comunicazioni. Questo tipo di attacco può essere utilizzato per interrompere operazioni e sistemi critici e bloccare l’accesso a siti web sensibili da parte di civili, militari e personale di sicurezza, o enti di ricerca.
- ##### Attacchi di propaganda
	Si sostanziano in tentativi di controllare le menti e i pensieri delle persone che vivono o combattono per un paese bersaglio. La propaganda può essere usata per esporre verità imbarazzanti, diffondere bugie per far perdere reputazione alla vittima, e alle persone la fiducia nel proprio paese, o schierarsi con i nemici.
- ##### Attacchi all'economia
	La maggior parte dei sistemi economici moderni opera tramite computer. Gli aggressori possono prendere di mira le reti di computer degli istituti economici come i mercati azionari, i sistemi di pagamento, o le banche, per rubare denaro o bloccare le persone dall’accesso ai fondi di cui hanno bisogno.
- ##### **Attacchi a sorpresa**
	Lo scopo di questi attacchi è quello di effettuare un attacco massiccio che il nemico non si aspetta, permettendo all’attaccante di indebolire le sue difese. Può essere eseguito per preparare il terreno per un attacco fisico nel contesto della guerra ibrida.

#### Esempi di Cyber War

- [[STUXNET]]
- [[CENTRALE ELETTRICA UCRAINA]]
#### REFERENZE: https://www.cybersecurity360.it/nuove-minacce/cyberwar-cose-tipologie-di-attacchi-cibernetici-e-soluzioni-per-combattere-la-guerra-ibrida/, https://www.redhotcyber.com/post/soc-e-sistemi-ics-quali-componenti-del-sistema-devono-essere-assolutamente-collegati/