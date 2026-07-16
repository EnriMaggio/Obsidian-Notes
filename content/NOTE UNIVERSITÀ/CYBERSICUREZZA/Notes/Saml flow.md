#### Data: 19/11/2024 - 10:15

Il flusso di autenticazione può essere avviato dal fornitore di servizi o dal fornitore di identità

- ##### Flusso SAML avviato dal fornitore di servizi
	il fornitore avvia la procedura di accesso inviando una richiesta SAML al provider di identità
	
	1. ![[Pasted image 20241119103034.png]]
	2. ![[Pasted image 20241119103247.png]]
	3. ![[Pasted image 20241119103401.png]]
	4. L'utente fornisce le sue credenziali di accesso e il provider di identità lo autentica
	5. ![[Pasted image 20241119103917.png]]
	6. ![[Pasted image 20241119104151.png]]
- ##### Flusso SAML avviato dal provider di identità
	1. L'utente accede al provider di identità.
	2. L'utente fa clic su un pulsante o un link per accedere al fornitore di servizi, ad esempio fa clic su un'app nella pagina Programma di avvio app in un'organizzazione Salesforce.
	3. Il provider di identità avvia la procedura di accesso inviando una risposta SAML  con firma crittografata al fornitore di servizi. La risposta SAML contiene un'asserzione SAML che comunica al fornitore di servizi l'identità dell'utente.
	4. Il fornitore di servizi convalida la firma della risposta SAML e identifica l'utente.
	5. Ora l'utente è connesso al fornitore di servizi.

#### Richiesta SAML

![[Pasted image 20241119104827.png]]
### **1. `<saml2p:AuthnRequest>`**
Questo è l'elemento principale della richiesta SAML. Indica che il messaggio è una richiesta di autenticazione da parte dello _Service Provider_ (SP) verso l'_Identity Provider_ (IdP).
### **2. `xmlns:saml2p`**
Questo attributo definisce lo _namespace_ XML del protocollo SAML utilizzato. Nel caso specifico: Indica che si sta utilizzando la versione 2.0 del protocollo SAML.
### **3. `xmlns:saml2`**
Simile al precedente, definisce lo _namespace_ XML per le _asserzioni_ SAML (cioè i dati di identità e attributi scambiati). È anche conforme alla versione 2.0
### **4. `ID`**
Questo campo specifica un identificativo univoco per la richiesta SAML, Serve a tracciare la richiesta e ad assicurare che non venga ripetuta (protezione contro _replay attacks_).
### **5. `Version`**
Indica la versione del protocollo SAML in uso. Nel caso specifico si sta utilizzando SAML 2.0, la versione più moderna e comune.
### **6. `IssueInstant`**
Questo campo specifica l'istante esatto in cui la richiesta è stata generata. L'orario è indicato in formato **UTC ISO-8601**:
### **7. `Destination`**
Indica l'URL dell'_Identity Provider_ (IdP) a cui la richiesta viene inviata
### **8. `AssertionConsumerServiceURL`**
Questo campo specifica l'endpoint del _Service Provider_ dove l'IdP deve inviare la risposta SAML (contenente l'asserzione di autenticazione):
### **9. `ProtocolBinding`**
Definisce il metodo con cui la risposta SAML sarà restituita dallo IdP al SP. Nel caso specifico indica che il metodo sarà **HTTP POST**, dove i dati saranno inviati tramite un form HTTP.
### **10. `<saml2:Issuer>`**
Indica chi ha generato questa richiesta, ovvero l'identità del _Service Provider_

#### Risposta SAML

![[Pasted image 20241119110046.png]]
### **1. `<saml2p:Response>`**
Indica che il messaggio è una risposta da parte dell'_Identity Provider_ (IdP) verso il _Service Provider_ (SP). Questo messaggio contiene l'esito della richiesta di autenticazione e, se il processo ha avuto successo, include l'asserzione SAML con i dettagli di autenticazione.
### **2. `xmlns:saml2p` e `xmlns:saml2`**
- **`xmlns:saml2p`**: Indica lo _namespace_ del protocollo SAML, che è la versione 2.0
- **`xmlns:saml2`**: Indica lo _namespace_ per le asserzioni SAML, sempre versione 2.0
### **3. `ID`**
Questo è l'identificativo univoco per questa specifica risposta SAML,  serve per tracciare la risposta e verificarne l'unicità (importante per prevenire replay attacks).
### **4. `Version`**
La versione del protocollo SAML utilizzato per questa risposta
### **5. `IssueInstant`**
Specifica l'istante in cui l'IdP ha generato questa risposta. L'orario è indicato in formato **UTC ISO-8601**
### **6. `Destination`**
Indica l'URL del _Service Provider_ (SP) a cui questa risposta SAML è destinata
In questo caso, la risposta sarà inviata all'endpoint `/saml/acs` del SP, come specificato nella richiesta originle
### **7. `InResponseTo`**
Questo campo collega questa risposta SAML a una richiesta SAML specifica. Qui fa riferimento all'`ID` della richiesta ricevuta in precedenza. Permette al SP di verificare che la risposta corrisponda alla richiesta inviata.
### **8. `<saml2:Issuer>`**
Indica l'entità che ha generato questa risposta, ovvero l'_Identity Provider_ (IdP)

### **9. `<saml2p:Status>`**

Questo elemento rappresenta lo stato del processo di autenticazione. È composto da:

- **`<saml2p:StatusCode>`**: Indica l'esito dell'operazione (lo stato). Nel caso specifico:
    `<saml2p:StatusCode Value="urn:oasis:names:tc:SAML:2.0:status:Success" />`
    Significa che l'operazione è avvenuta con successo.

Se ci fosse stato un errore, questo campo avrebbe un valore diverso, ad esempio:
- `urn:oasis:names:tc:SAML:2.0:status:Requester` (richiesta non valida),
- `urn:oasis:names:tc:SAML:2.0:status:Responder` (errore lato IdP).

### **10. `<saml2:Assertion>`**

L'asserzione SAML contiene i dettagli relativi all'autenticazione dell'utente. In questo caso è rappresentata come un commento:
`<!-- user and authentication details -->`

Di solito, l'asserzione include informazioni come:

- Identità dell'utente (nome utente, e-mail, ecc.).
- Attributi aggiuntivi (ruoli, gruppi, ecc.).
- Dettagli della sessione (ad esempio, validità temporale).

#### Asserzione SAML

![[Pasted image 20241119111327.png]]
### **1. `<Assertion>`**

Rappresenta il nucleo del messaggio SAML e contiene tutte le informazioni principali sull'utente autenticato e sull'autenticazione stessa. Le informazioni sono strutturate in vari blocchi come `Subject`, `Conditions`, `AttributeStatement` e `AuthnStatement`.
#### **Attributi principali**

- **`xmlns`**: Specifica lo _namespace_ dell'asserzione
- **`ID`**: Identificativo univoco dell'asserzione, utile per il tracciamento e per evitare attacchi di replay
- **`Version`**: Versione del protocollo SAML utilizzato, in questo caso:
- **`IssueInstant`**: Timestamp di quando l'asserzione è stata emessa dall'IdP (in formato ISO-8601 UTC)
### **2. `<Issuer>`**
Specifica l'identità dell'entità che ha emesso l'asserzione, ovvero l'Identity Provider (IdP). L'IdP si identifica tramite un URL (in genere l'endpoint SAML).

### **3. `<Subject>`**
Contiene le informazioni sull'utente autenticato (il "soggetto" della SAML assertion). In questo esempio è rappresentato come un commento:

`<Subject><!-- user details --></Subject>`

Tipicamente, include:

- **`NameID`**: L'identità dell'utente (es. e-mail, nome utente, ecc.).
- **`SubjectConfirmation`**: Specifica le condizioni che permettono al SP di accettare l'asserzione, ad esempio un token di conferma.
### **4. `<Conditions>`**
Definisce i vincoli temporali e di utilizzo per l'asserzione, inclusi:

- **`NotBefore`**: L'asserzione è valida a partire da questo orario.
- **`NotOnOrAfter`**: L'asserzione non è più valida dopo questo orario.

Serve a garantire che l'asserzione sia valida solo in un determinato intervallo temporale per evitare attacchi.
### **5. `<AttributeStatement>`**
Contiene gli **attributi dell'utente**. Questi sono dettagli aggiuntivi che l'IdP fornisce al SP, come il nome, il ruolo, i gruppi o qualsiasi altra informazione utile. Nel file è rappresentato come un commento:
`<AttributeStatement><!-- user details --></AttributeStatement>`

Un esempio reale potrebbe includere:
![[Pasted image 20241119112548.png]]
### **6. `<AuthnStatement>`**

Descrive i dettagli dell'autenticazione effettuata dall'IdP, come il metodo utilizzato (es. password, certificato, ecc.) e il momento in cui l'utente è stato autenticato:

`<AuthnStatement><!-- authentication details --></AuthnStatement>`

Tipicamente include:
- **`AuthnInstant`**: Quando l'utente è stato autenticato.
- **`SessionIndex`**: Un identificativo unico per la sessione di autenticazione.
- **`AuthnContextClassRef`**: Specifica il contesto di autenticazione (es. autenticazione a due fattori, password, ecc.)


#### REFERENZE: https://help.salesforce.com/s/articleView?id=sf.identity_provider_about.htm&type=5