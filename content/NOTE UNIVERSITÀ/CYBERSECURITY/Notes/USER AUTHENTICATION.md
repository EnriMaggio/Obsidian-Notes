#### Data: 11/11/2024 - 11:04

#### Gestione delle identità e degli accessi (Identity and Access Management)

è la disciplina di sicurezza che consente alle entità giuste (autorizzate) di utilizzare le risorse effettivamente assegnate a loro o che ne hanno diritto, nel momento in cui hanno bisogno, senza interferenze.

Comprende un insieme di tecnologie, tecniche e sistemi per gestire identità digitali da parte degli amministratori, i quali possono assegnare identità digitali a nuovi utenti all'interno dell'organizzazione

consiste di tre componenti:
- **Autenticazione**
- **Autorizzazione**
- **Controllo d'accesso**

#### Autenticazione
l'autenticazione ("auth" in breve) è il processo che verifica che un utente sia la persona che dichiara di essere. E importante per l'accountability nel sistema. 

Ci sono molti sistemi di autenticazione ma si basano sempre su tre principi:

1.  Innanzitutto, un nuovo utente deve creare un account all'interno di un sistema di autenticazione. Come parte della creazione di questo account, l'utente registra una serie di fattori di autenticazione, che possono variare da semplici password a token di sicurezza fisica e scansioni di impronte digitali. (Per ulteriori informazioni, vedi "Fattori di autenticazione".). Questi fattori dovrebbero essere conosciuti o posseduti solo dall'utente. In questo modo, il sistema di autenticazione può essere ragionevolmente sicuro che, se qualcuno può fornire questi fattori, questo sarà appunto l'utente.  

2. Il sistema di autenticazione memorizza le credenziali dell'utente in una directory o in un database, dove sono associate all'ID dell'utente e ad altri attributi importanti. Per motivi di sicurezza, i sistemi di autenticazione solitamente non memorizzano le credenziali come testo semplice. Memorizzano invece versioni con hash o crittografate, che risulterebbero meno utili in caso di furto da parte di hacker.   

3. Quando l'utente desidera accedere al sistema, fornisce il proprio ID utente e i fattori di autenticazione registrati. Il sistema di autenticazione verifica la voce della directory per questo ID utente, per vedere se le sue credenziali corrispondono a quelle salvate nella directory. In caso affermativo, il sistema di autenticazione verifica l'identità dell'utente.

#### Fattori di autenticazione

- ##### Fattori di conoscenza
	Sono informazioni che solo l'utente conosce come ad esempio password, pin
- ##### Fattori di possesso 
	Sono cose o oggetti che un utente possiede, di solito sono dispositivi hardware che forniscono token di sicurezza, molte persone utilizzano dispositivi mobili che utilizzano app di autenticazione che generano password monouso OTP
- ##### Fattori di inerenza
	Sono le caratteristiche fisiche esclusive dell'utente, comprende tutti i metodi di autenticazione biometrici per l'autenticazione attraverso la scansione facciale o impronta digitale
- ##### Fattori comportamentali 
	Questi fattori seguono modelli comportamentali come l'intervallo di indirizzi IP tipico di una persona, le ore di attività e la velocità media di digitazione.

#### Autenticazione a più fattori

I metodi di [autenticazione a più fattori](https://www.ibm.com/it-it/topics/multi-factor-authentication) (MFA) richiedono almeno due fattori di almeno due tipi diversi. Il sistema MFA è considerato più robusto dell'SFA in quanto gli hacker devono rubare più credenziali per assumere il controllo degli account degli utenti. I sistemi MFA tendono inoltre a utilizzare credenziali che sono molto più difficili da rubare rispetto alle password.

Maggiormente si utilizza l'autenticazione a 2 fattori, è la soluzione più sicura che abbiamo oggi ma comunque presenta delle vulnerabilità

Il secondo fattore consiste con l'utilizzo di un dispositivo (usb), oppure appoggiandosi alle caratteristiche biometriche o con l'utilizzo di un app che fornisce il secondo fattore disponibile in piccolo intervallo di tempo

#### Aumento di attacchi ai sistemi con password

![[Pasted image 20241111125223.png]]

#### Autenticazione con password

L'autenticazione di password nonostante sia quella più attaccata è comunque molto comoda al giorno d'oggi, perchè ormai usiamo tanti servizi che usano account e sono anche semplici da implementare e meno costosi

Consiste che l'utente fornisce le sue credenziali (username e password) e il sistema compara le credenziali fornite dall'utente con quelle salvate nel suo database oppure nel password file per verificare l'autenticità (la password è sempre salvata cifrata e mai in chiaro)

![[Pasted image 20241111131126.png]]

#### Problematiche con l'autenticazione con password

Le persone in media sono registrati a tanti siti o servizi, in media 22. Questo porta all'utente a fare uno sforzo cognitivo per ricordarsi tutte le password e quindi cade nella trappola di utilizzare password prevedibili o molto semplici

![[Pasted image 20241111131650.png]]
![[Pasted image 20241111131745.png]]

La cosa peggiore è che se già si usano password "facili", gli utenti tendono a usare le stesse password per siti diversi (magari anche importanti come quelli di lavoro o banking), questo permette all'attaccante di avere più obiettivi o possibilità di attacco

#### Tipi di attacco ai sistemi di autenticazione con password

![[Pasted image 20241111132917.png]]

#### Dove vengono salvate le password nel sistema operativo

Su windows le password vengono salvate nel SAM (Security account manager) ovvero un database file che salva le password degli utenti. Questo file risiede sotto la directory System32/config ed è montata su HKLM/SAM e ci vogliono i privilegi di sistema per visualizzare questo file


Il Sam può essere salvato nei registri di windows, in questo modo gli attaccanti potrebbero fare una copia con il comando reg

L'hashing di windows ha avuto due versioni

![[Pasted image 20241111134705.png]]

#### Password su linux

Linux salva le password (ovviamente cifrate) degli utenti su etc/shadow, mentre nel file etc/passwd vengono salvate le informazioni dell'utente ovvero nomi utente, cartella home e la shell predefinita

![[Pasted image 20241111135248.png]]
![[Pasted image 20241111135443.png]]
![[Pasted image 20241111135521.png]]

#### Tipi di attacco alle password

- ##### Attacco forza bruta
	Questo attacco consiste di conoscere innanzitutto la politica dell'azienda nel formare password e poi provare per ogni combinazione possibile per craccare la passsword
	![[Pasted image 20241111141437.png]]
- ##### Attacco con dizionario
	Gli attaccanti utilizzano un dizionario con frasi e parole comunemente usate  per indovinare le possibili password, lo svantaggio è che se le parole nel dizionario non matchano la password da violare non funziona
	![[Pasted image 20241111141849.png]]
- ##### Attacco ibrido 
	Sempre utilizzando il dizionario, l'attaccante prende le parole e le modifica seguendo dei pattern che gli utenti di solito utilizzano per la creazione delle loro password
- ##### Tabelle rainbow
	è come l'attacco di hash ma al posto delle parole, ci sono già le loro versioni hashate ma occupano tantissima memoria
- ##### Pass the hash
	Sfruttano gli hash dell'ntlm
	![[Pasted image 20241111150549.png]]

#### Password forte

![[Pasted image 20241111151020.png]]

L'entropia non ci basta a quantificare quanto è forte una password alla fine

#### ZXCVBN

È uno strumento per stimare la robustezza delle password, ispirato ai metodi utilizzati dai programmi per violare le password. Attraverso il riconoscimento di schemi e una stima conservativa, identifica e valuta 30.000 password comuni, nomi e cognomi frequenti secondo i dati del censimento statunitense, parole inglesi popolari tratte da Wikipedia, serie televisive e film statunitensi, e altri schemi ricorrenti come date, ripetizioni (aaa), sequenze (abcd), combinazioni di tastiera (qwertyuiop) e linguaggio leet (l33t speak).

Utilizza diversi pattern utilizzati dagli utenti per creare le proprie password

![[Pasted image 20241111152055.png]]

Per stimare le password dropbox prova a identificare i pattern utilizzati
![[Pasted image 20241111152347.png]]

Poi stabilisce una stima di quanti tentativi l'attaccante deve fare per identificare ogni pattern

![[Pasted image 20241111152511.png]]

Poi vanno a considerare i pattern che combinandoli nel minor numero di tentavi possibili andava a ricreare la password

![[Pasted image 20241111153557.png]]

#### Prevenzione agli attacchi offline

Per contrastare il brut force e i dizionari si può aggiungere del Salt alla password

![[Pasted image 20241111154556.png]]

#### Credential stuffing

![[Pasted image 20241111155032.png]]

#### Password spraying

Il password spray, noto anche come attacco di password spray, si verifica quando un malintenzionato utilizza password comuni per tentare di accedere a diversi account su un dominio. Utilizzando un elenco di password deboli comunemente usate, come 123456 o password1, un malintenzionato può potenzialmente accedere a centinaia di account con un unico attacco.

Se un criminale informatico riesce ad accedere a uno solo dei vostri account, potrebbe avere accesso a tutti i vostri dati:

![[Pasted image 20241111155331.png]]

#### Possibili contromisure

si può:
- Cambiare spesso password
- Farsi generare la password
- Utilizzare politiche di password forti

anche se non ancora sicure al 100%

#### Soluzione definitiva

La soluzione consiste di utilizzare e combinare 3 parole che siano facilmente ricordabili, un altro vantaggio è che la password risulterà lunga

Altre contromisure effettivamente effettive sono
![[Pasted image 20241111160130.png]]
#### REFERENZE: https://www.ibm.com/it-it/think/topics/authentication, https://www.ibm.com/it-it/topics/identity-access-management, https://www.ninjaone.com/it/blog/cos-e-un-attacco-mfa-fatigue/, https://en.wikipedia.org/wiki/Security_Account_Manager, https://learn.microsoft.com/it-it/troubleshoot/windows-server/windows-security/ntlm-user-authentication