#### Data: 14/10/2024 - 09:46

#### COSA E:
Il framework MITRE ATT&CK è una ==**base di conoscenza**== universalmente ==**accessibile**== e costantemente aggiornata per modellare, rilevare, impedire e ==**contrastare**== le minacce alla [cybersecurity](https://www.ibm.com/it-it/topics/cybersecurity) sulla base dei comportamenti antagonisti noti dei criminali informatici.

L'_ATT&CK_ in MITRE ATT&CK è l'acronimo di _Tattiche avverse_, _Tecniche e conoscenza comune_.

#### COME E STRUTTURATO:
E strutturato in tre matrici:

- ##### Matrice Enterprise 
	Include tutte le tecniche degli avversari utilizzate negli attacchi contro l'infrastruttura aziendale. Questa matrice include sottomatrici per piattaforme Windows, macOS e Linux, nonché infrastrutture di rete, piattaforme cloud e tecnologie [container](https://www.ibm.com/it-it/topics/containers). Include inoltre una matrice PRE di tecniche preparatorie utilizzate prima di un attacco.
- ##### MATRICE MOBILE
	La matrice Mobile include tecniche utilizzate negli attacchi diretti ai dispositivi mobili e negli attacchi mobili basati sulla rete che non richiedono l'accesso a un dispositivo mobile. Questa matrice include sottomatrici per le piattaforme mobili iOS e Android.
- ##### MATRICE ICS
	La Matrice ICS include tecniche utilizzate negli attacchi ai sistemi di controllo industriale, in particolare macchinari, dispositivi, sensori e reti utilizzati per controllare o automatizzare le operazioni per fabbriche, utenze, sistemi di trasporto e altri fornitori di servizi critici.

Ci concentreremo su [enterprise matrix](https://attack.mitre.org/matrices/enterprise/)

#### OBBIETTIVO:
L'obbiettivo di questo framework è quello di ==**catalogare**== i seguenti aspetti:
- [[TATTICHE]]
- [[TECNICHE]]
- procedure dei criminali informatici

I primi due vengono ==**organizzati in Matrici**==. Questi tre aspetti sono presenti in ogni ciclo vitale di un'attacco informatico. Con queste informazioni il MITRE ATT&CK è in grado di aiutare e fornire assistenza ai team di sicurezza delle varie aziende:
- a ==**simulare**== accuratamente gli attacchi informatici per ==**testare le difese**== informatiche;
- a ==**creare**== criteri e controlli di sicurezza e piani [di risposta agli incidenti più efficaci](https://www.ibm.com/it-it/topics/incident-response)
- a ==**scegliere e configurare le tecnologie di sicurezza**== per rilevare, impedire e mitigare meglio le minacce informatiche.
#### DIFFERENZA CON CYBER KILL CHAIN:
Come MITRE ATT&CK, Lockheed Martin Cyber Kill Chain modella gli attacchi informatici come una serie di tattiche avversarie. Alcune tattiche hanno addirittura gli stessi nomi. Ma l'analogia finisce qui.

La Cyber Kill Chain è più di un semplice framework che una base di conoscenza. È molto meno dettagliato di MITRE ATT&CK. Interessa solo sette (7) tattiche: _Riconoscimento, Weaponizzazione, Consegna, Sfruttamento, Installazione, Comando e Controllo, Azioni su obiettivi,_rispetto a MITRE ATT&CK 18 (incluse solo le tattiche Mobile e ICS). Non fornisce modelli discreti per gli attacchi su piattaforme Mobile o ICS. E non cataloga nulla che si avvicini al livello di informazioni dettagliate in merito a tattiche, tecniche e procedure presenti in MITRE ATT&CK.

Un'altra importante distinzione: la Cyber Kill Chain si basa sul presupposto che un attacco informatico deve realizzare tattiche avversarie in sequenza per raggiungere un risultato positivo e che il blocco di una delle tattiche "spezzerà la kill chain" e impedirà all'avversario di raggiungere l'obiettivo finale. MITRE ATT&CK non adotta questo approccio; si concentra sull'aiutare i professionisti della sicurezza a identificare e bloccare o mitigare le singole tattiche e tecniche avversarie in qualsiasi contesto si presentino.

REFERENZE: https://www.ibm.com/it-it/topics/mitre-attack



