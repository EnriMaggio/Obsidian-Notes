È la versione sicura di [http](https://it.wikipedia.org/wiki/Hypertext_Transfer_Protocol), per sicuro si intende che la comunicazione tra browser del client e server non avviene più in chiaro, ma avviene in maniera crittografata. Tutte le comunicazioni con questo protocollo sono criptate. Per garantire questa sicurezza, http si appoggia sul protocollo TLS. I dati inviati usando https hanno le seguenti caratteristiche:

- **Crittografia**
	i dati scambiati vengono codificati per essere resistenti dai eavesdroppers. La crittografia copre l'URL del documento richiesto, anche il suo contenuto, i contenuti dei form del browser, i cookies e infine il contenuto dell'header HTTP
- **Data integrity**
	I dati non vengono modificati, o meglio manomessi, durante il trasferimento. Inoltre non possono essere eliminati
- **Autenticazione**
	Dimostra che gli utenti comunicano con il website atteso. Protegge da attacchi man in the middle.
	
---
### Iniziazione connessione

Il browser agent funge quindi da client HTTP e anche da client TLS. Nella pratica, all'inizio si segue obbligatoriamente il protocollo handshake di TLS per stabilire una comunicazione sicura, per poi iniziare lo scambio di messaggi con il protocollo HTTP che invia messaggi criptati.

Brevemente, il client avvia una connessione al server sulla porta appropriata e quindi invia il TLS ClientHello per avviare l'handshake TLS. Al termine dell'handshake TLS, il client può quindi avviare la prima richiesta HTTP. Tutti i dati HTTP devono essere inviati come dati applicativi TLS. È necessario seguire il normale comportamento HTTP, incluse le connessioni mantenute.

![[Pasted image 20251106155407.png]]

Ci sono tre livelli di consapevolezza di una connessione in HTTPS
1. A livello HTTP, un client HTTP richiede una connessione a un server HTTP inviando una richiesta di connessione al livello immediatamente inferiore. In genere, il livello immediatamente inferiore è TCP, ma può anche essere TLS/SSL.
2. A livello TLS, viene stabilita una sessione tra un client TLS e un server TLS. Questa sessione può supportare una o più connessioni in qualsiasi momento.
3. Una richiesta TLS per stabilire una connessione inizia con la creazione di una connessione TCP tra l'entità TCP sul lato client e l'entità TCP sul lato server


---
### Chiusura connessione

La chiusura della connessione può essere indotta da ambo i lati includendo nel record HTTP la linea *Connection: close.* che indica che la connessione sarà chiusa appena questo record sarà ricevuto.

Chiudere una connessione https significa che prima bisogna chiudere la connessione TLS tra le entità peer, di conseguenza si chiuderà anche la connessione TCP

A livello TLS, il modo consono per concludere la connessione è che entrambi i peer utilizzano il protocollo TLS alert per mandare un messaggio di alert *close_notify*. La implementazione TLS può, dopo un messaggio di alert, chiudere la connessione senza aspettare l'alert closuse dell'altro peer, generando un "incomplete close". I client http devono quindi rispondere nel caso la connessione TCP è terminata con l'alert *close_notify* (e senza l'indicatore *Connection: close.*). Una chiusura TCP non annunciata può essere evidenza di un qualche tipo di attacco, così facendo il client https dovrebbe emettere una sorta di avviso di sicurezza quando
questo accade  


