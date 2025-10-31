Kerberos è un protocollo di rete per l'autenticazione forte che permette a diversi terminali di comunicare su una rete informatica insicura provando la propria identità mediante l'utilizzo di tecniche di crittografia simmetrica. Kerberos previene attacchi quali l'intercettazione e i replay attack ed assicura l'integrità dei dati.

Questo protocollo fornisce un server di autenticazione centralizzato la cui funzione è quella di autenticare utenti ai server e server agli utenti

Il primo report su kerberos stilò le seguenti specifiche:

- **Sicuro** (**Secure**): Un intercettatore di rete non dovrebbe essere in grado di ottenere le informazioni necessarie per impersonare un utente. Più in generale, Kerberos dovrebbe essere abbastanza forte da far sì che un potenziale avversario non lo consideri l'anello debole.
    
- **Affidabile** (**Reliable**): Per tutti i servizi che si affidano a Kerberos per il controllo degli accessi, la mancanza di disponibilità del servizio Kerberos comporta la mancanza di disponibilità dei servizi supportati. Perciò, Kerberos dovrebbe essere altamente affidabile e dovrebbe impiegare un'architettura di server distribuiti con un sistema in grado di eseguire il backup di un altro
    
- **Trasparente** (**Transparent**): Idealmente, l'utente non dovrebbe essere consapevole che l'autenticazione sta avvenendo, al di là della necessità di inserire una password. L'unica cosa che nota sono piccoli tempi di delay
    
- **Scalabile** (**Scalable**): Il sistema dovrebbe essere in grado di supportare un gran numero di client e server. Ciò suggerisce un'architettura modulare e distribuita

Per supportare queste specifiche, lo schema di kerberos è quello di un servizio di autenticazione di terze parti fidato che usa un protocollo basato su Needham and Schroeder


---
### Kerberos versione 4

Questa versione di kerberos fa uso dell'algoritmo DES per la crittografia per fornire il servizio di autenticazione. Il protocollo fa uso di vari componenti per il suo funzionamento:

- **Server di Autenticazione (AS) / Authentication Server (AS)**
    - Conosce le **password** di tutti gli utenti e le memorizza in un database centralizzato.
    - Condivide una **chiave segreta** unica con ogni server.
        
- **Ticket**
    - Creato una volta che l'AS accetta l'utente come autentico; contiene l'**ID dell'utente** e l'indirizzo di rete e l'**ID del server**.
    - **Crittografato** utilizzando la chiave segreta condivisa dall'AS e dal server.
        
- **Server di Concessione Ticket (TGS) / Ticket-granting server (TGS)**
    - Rilascia ticket agli utenti che sono stati **autenticati dall'AS**.
    - Ogni volta che l'utente richiede l'accesso a un nuovo servizio, il client si rivolge al TGS utilizzando il **ticket per autenticarsi**.
    - Il TGS concede quindi un **ticket per il particolare servizio**.
    - Il client salva ogni ticket di concessione del servizio e lo utilizza per **autenticare il suo utente** a un server ogni volta che viene richiesto un particolare servizio.

Il processo completo di kerberos è la seguente

![[Pasted image 20251021174802.png]]

Gli utenti spesso vogliono accedere a risorse o servizi nella rete, per farlo devono prima passare dalla KDC che è composta da
- **Authentication server (AS)**
	Questo server si accerta e conferma che un utente conosciuto sta facendo una richiesta d'accesso, una volta autenticato, il server consegna all'user un ticket
- **Ticket Granting Server (TGS)**
	invece questo server si accerta che l'utente stia facendo una richiesta d'accesso ad un servizio o a una risorsa, consegnando all'utente un ticket di servizio

Il sequence diagram è il seguente 

![[Pasted image 20251022160717.png]]

In tutto ci sono 6 passi. Nel dettaglio, i contenuti dei messaggi scambiati è la seguente

![[Pasted image 20251021175916.png]]

Il client (C) invia all'authentication server un messaggio in chiaro contenente il suo identificativo, l'identificativo del server tgs e il timestamp del messaggio inviato. In seguito l'AS controlla nella sua tabella dove ci sono gli utenti con le loro relative chiave segrete condivise con il server, la corrispondenza con l'identificativo inviato da C. Con questa chiave l'AS cripta il messaggio da inviare a C, che contiene:
- chiave di sessione condivisa tra C e TGS
- l'identificativo di TGS
- timestamp2 di questo nuovo messaggio da inviare ancora
- lifetime2 del ticket
- il ticket per TGS
	questo ticket a sua volta è criptato con la chiave condivisa con TGS e contiene:
	- chiave di sessione condivisa tra C e TGS
	- identificatio di C
	- indirizzo ip di C
	- identificativo TGS
	- lo stesso timestamp2
	- lo stesso lifetime2
A questo punto AS spedisce a C il ticket-granting ticket e la session key. Sicome la chiave di sessione è all'interno del messaggio criptato con Kc, solo C riesce a leggere quel messaggio

![[Pasted image 20251022152519.png]]

C decripta il messaggio con la sua chiave ottenendo quindi il ticket per il server TGS che contiene all'interno la chiave di sessione tra C e TGS, in seguito manda al TGS un messaggio composta da:
- identificativo ID della risorsa da ottenere
- ticket
- autenticatore che comprende ID, indirizzo e un timestamp
L'utenticatore, a differenza del ticket, è usato una sola volta e ha un tempo di vita molto breve. Il TGS, una volta ricevuto il messaggio, decodifica il ticket con la chiave che condivide con AS, il ticket in parole povere dichiara che chi usa la chiave condivisa tra C e TGS deve essere per forza C. Quindi il TGS a questo punto è sicuro che il messaggio è stato inviato correttamente e che proviene da C.  Inoltre il TGS usa la chiave di sessione per decodificare l'autenticatore di C così riesce a confrontare i valori all'interno di esso con i valori del ticket.

Se tutto corrisponde, il TGS è pronto a spedire a C un messaggio codificato (con la chiave condivisa tra C e TGS) simile alla fase 2
- chiave di sessione condivisa tra C e V
- identificativo di V
- timestamp4
- ticket della risorsa V (contiene anche questo la chiave di sessione tra C e V)

C ora possiede un service-granting ticket riusabile per V

![[Pasted image 20251022155311.png]]

C oltre a mandare il ticket per la risorsa v, manda di nuovo un autenticatore. Questo perchè l'autenticatore è l'unico modo per autenticare la identità del messaggio. Il ticket viene decodificato dal server,in seuguito recupera la chiave di sessione e decodifica l'autenticatore per confrontare i valori IDC, ADC.

Il server risponde a C con un messaggio criptato con la chiave condivisa tra C e V, se serve l'autenticazione mutuale, il server invia il valore del timestamp5 sommatto con uno all'interno del messaggio


---
### kerberos realms

Un kerberos realm è un ambiente in cui sono presenti più server kerberos, più utenti e più application server.

Per avere tale ambiente è necessario che
- i server kerberos devono avere l'ID dell'utente e la password hashed di tutti gli utenti partecipanti nel suo database. tutti gli utenti sono registrati con i sever kerberos
- i server kerberos devono condividere una chiave segreta con ogni server. Tutti i server devono essere registrati con i server kerberos

Il realm è quindi un insieme di nodi che condividono lo stesso database kerberos. quest'ultimo risiede nel kerberos master computer system (centralizzato)

Questa infrastuttura permette a utenti di un realm di richiedere un serivizio o una risorsa localizzata in un altro realm di un altro dominio in modo sicuro.

In fine lo schema completo richiede che i server kerberos di un realm si fidano del server kervberos di un altro realm per autenticare i suoi utenti. Ovviamente il secondo realm deve fidarsi dei server kerberos del primo realm.

Se un utente richiede un servizio di un altro realm, l'utente deve ottenere il ticket per il server di quel realm. Il TGS del realm dell'utente invia il ticket per il TGS remoto dell'altro realm

![[Pasted image 20251022162133.png]]

L'approccio dei realm ha l'unico difetto che non scala efficientemente all'aumentare del numero dei realm. Questo perchè se ci fossero N realms, allora ci devono essere $N(N-1)/2$
chiave sicure scambiate tra i vari server. Ogni server TGS deve avere una chiave scambiata con gli altri TGS 