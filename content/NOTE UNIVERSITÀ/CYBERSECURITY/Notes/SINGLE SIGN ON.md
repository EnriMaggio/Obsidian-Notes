#### Data: 19/11/2024 - 09:02

#### Problema

Quando si parla di autenticazione rimane comunque il problema che l'utente deve ricordarsi e mantenere più password forti per diversi servizi account ecc. ecc.

![[Pasted image 20241119091239.png]]

#### Soluzione

Nel corso del tempo quindi si è cercato di trovare soluzione alternative che riguardassero sistemi centralizzati per l'autenticazione anche in più piattaforme

![[Pasted image 20241119091637.png]]

#### Identità digitale

Per implementare questa soluzione centralizzata abbiamo bisogno di una identità digitale, una sorte di chiave sicura che ci permette di accedere a varie porte di servizi noti e pubblici

Consiste in una serie di attributi o dati, associati in maniera univoca ad un utente (ovviamente questo gli differenzia dagli altri utenti). Questi dati vengono memorizzati e condivisi digitalmente all'interno di un ecosistema di attori e attraverso tecnologie abilitanti.

#### Digital identity management

Un sistema di gestione di identità digitali fornisce una soluzione centralizzata che permette di creare, mantenere e usare le identità digitali in un contesto legale. Non solo si occupa di gestire queste identità ma gestisce anche l'accesso e la verifica da parte di un utente a risorse e servizi

In un contesto aziendale IT, l'obbiettivo principale è identificare un utente, autenticarlo e autorizzarlo all’accesso secondo il profilo e ruolo della sua identità digitale. Una volta stabilita, l’identità digitale deve essere mantenuta, modificata e monitorata in ogni momento del ciclo di vita del procedimento di accesso, ovvero durante il provisioning del servizio, l’onboarding dell’utenza e il suo offboarding e cancellazione al momento appropriato.

Gli attori coinvolti nel digitale identity management sono
- utente: entità digitale
- identity provider: è un sistema che permette di creare, salvare e gestire identità digitali
- service provider:  sono tutte applicazioni di terze parti che forniscono un servizio all'utente

#### Single Sign On (SSO) 

E un processo, una schema di autenticazione in cui l'utente ha bisogno di accedere e autenticarsi una volta sola, tramite un unico set di credenziali, una volta fatto ciò oltre ad accedere alle sue risorse autorizzate l'utente non ha più bisogno di autenticarsi una seconda volta, perchè è il compito viene delegato all'Identity provider 

Ovviamente per l'utente è una esperienza molto semplice e veloce

![[Pasted image 20241119094417.png]]

![[Pasted image 20241119094504.png]]

#### Come funziona il SSO

é basato da un'accordo, su una relazione di fiducia tra diversi **provider di servizi** (applicazioni, siti web) e **provider di identità**

questo porta a vari vantaggi
- condivisione facile dell'identità tra diverse organizzazioni
- un utente che accede ad una organizzazione, può accedere alle sue sotto organizzazioni
- riduce costi di mantenimento di identità
- più sicuro

  
In generale, l'autenticazione SSO funziona come segue:

1. Un utente accede a uno dei provider di servizi o a un portale centrale (come un portale aziendale intranet o per studenti universitari) tramite le credenziali di accesso SSO.  
     
2. Quando l'utente viene autenticato, la soluzione SSO genera un token di autenticazione della sessione contenente informazioni specifiche sull'identità dell'utente (nome utente, indirizzo e-mail, ecc.). Questo token viene memorizzato nel browser web dell'utente o nel sistema SSO.  
     
3. Quando l'utente tenta di accedere a un altro fornitore di servizi affidabile, l'applicazione verifica con il sistema SSO per determinare se l'utente è già autenticato per la sessione. In tal caso, la soluzione SSO convalida l'utente firmando il token di autenticazione con un certificato digitale e all'utente viene concesso l'accesso all'applicazione. In caso contrario, all'utente viene richiesto di immettere nuovamente le credenziali di accesso.

#### Saml

Abbiamo visto teoricamente come funziona, uno dei protocolli che permettono l'sso è il **SAML**, ovvero un protocollo standard basato su XML usato per lo scambio di dati crittografati di autenticazione e autorizzazione tra un provider di identità e più provider di servizi 

[[Saml flow]]

#### OAuth

E un protocollo standard di autenticazione aperto che consente ad un utente di concedere ad un sito web o ad un'applicazione di terze parti l'accesso alle proprie risorse protette (in un server http), senza rilevare a terzi le proprie credenziali o identità.

Il suo compito non è quello di autenticarsi, piuttosto è un protocollo di Autorizzazione

In un tipico scenario OAuth 2.0, l’utente avvia il processo cliccando su un pulsante o un link all’interno dell’applicazione client. Questo reindirizza l’utente al server di autorizzazione (Viene richiesto un token di accesso dal server di autenticazione), dove viene visualizzata una richiesta di autorizzazione che specifica le risorse a cui l’applicazione client desidera accedere.

Se l’utente concede l’autorizzazione, il server di autorizzazione verifica l’identità dell’utente e genera un token di accesso. Il token viene quindi inviato in modo sicuro all’applicazione client, che può utilizzarlo per accedere alle risorse autorizzate sul server web.

Gli attori in una richiesta di autorizzazione sono:
- **proprietario delle risorse**: entità che è in grado di dare permesso al client
- **client**: applicazione di terze parti che fa la richiesta di accesso(in seguito dell'autorizzazione del proprietario) alle risorse protette
- **Server di autorizzazione**: il server una volta autenticato l'identità restituisce un token al client
- **Server di risorse**: ci sono le risorse protette del proprietario

#### OpenID Connect

può essere visto come un livello di identità costruito in cima al protocollo OAuth 2.0 e consente ai client di verificare l’identità dell’utente finale in base all’autenticazione eseguita da un server di autorizzazione, ma anche di ottenere informazioni di base sul profilo dell’utente finale in modo interoperabile.

In sostanza ci permette anche di registrare a delle applicazioni di terze parti usando già account esistenti disponibili da parte dell'utente (google, microsoft)

Trattandosi di un protocollo standard, OpenID Connect consente ai client di tutti i tipi, compresi quelli basati su Web, dispositivi mobili e JavaScript, di richiedere e ricevere informazioni sulle sessioni autenticate e sugli utenti finali.

#### Flussi di autorizzazione
- [[Authorization Code Grant Flow]]
- [[Authorization Code Grant Flow with PCKE]]
- [[Resource Owner Password]]
- [[Client credential Flow]]
- [[Device Flow]]

#### REFERENZE: https://blog.osservatori.net/it_it/identita-digitale-significato-funzionamento, https://www.cybersecurity360.it/soluzioni-aziendali/oauth-2-0-cose-e-come-funziona-lo-standard-aperto-per-lautenticazione-sicura-online/, https://www.cybersecurity360.it/soluzioni-aziendali/openid-connect-cose-a-cosa-serve-e-perche-e-importante/