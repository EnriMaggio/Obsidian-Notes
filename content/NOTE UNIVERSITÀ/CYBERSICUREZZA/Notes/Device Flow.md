#### Data: 19/11/2024 - 17:05

Questo flusso viene utilizzato in cui la richiesta di accesso ad alcune risorse nel contesto in cui ci sono dei dispositivi con interfaccia limitata lato input (smart tv).

I dispositivi quindi chiedono all'utente di andare in un link su un'altro dispositivo (pc, telefono ecc. ecc.)

Ci sono due flussI per fare questa autorizzazione
#### richiesta da parte del dispositvo
1. L'utente avvia l'app sul dispositivo.
2. L'app del dispositivo richiede l'autorizzazione al **Authorization Server** utilizzando il proprio **Client ID** (endpoint `/oauth/device/code`).
3. Il **Auth0 Authorization Server** risponde con:
    - un **device_code**,
    - un **user_code**,
    - un **verification_uri**,
    - un **verification_uri_complete**,
    - un **expires_in** (tempo di validità in secondi per il **device_code** e lo **user_code**),
    - e un intervallo di polling (**polling interval**).
    
4. L'app del dispositivo chiede all'utente di attivarsi utilizzando un computer o uno smartphone. L'app può farlo:
	- chiedendo all'utente di visitare il **verification_uri** e inserire lo **user_code**, dopo aver mostrato questi valori sullo schermo;
    - chiedendo all'utente di interagire con un **QR Code** o un URL abbreviato contenente lo **user_code** generato dal **verification_uri_complete**;
    - navigando direttamente alla pagina di verifica con lo **user_code** incorporato utilizzando il **verification_uri_complete**, se l'app è in esecuzione su un dispositivo basato su browser.

5. L'app del dispositivo inizia a fare polling sul tuo **Authorization Server** per un **Access Token** (endpoint `/oauth/token`) utilizzando l'intervallo di tempo specificato da **interval** e contando a partire dalla ricezione dell'ultima risposta di polling. L'app continua il polling fino a quando:
    - l'utente completa il flusso nel browser, oppure
    - lo **user_code** scade.
- Quando l'utente completa con successo il flusso nel browser, il tuo **Auth0 Authorization Server** risponde con un **Access Token** (e opzionalmente un **Refresh Token**). L'app del dispositivo dovrebbe ora dimenticare il **device_code**, poiché sarà scaduto.
    
- L'app del dispositivo può utilizzare l'**Access Token** per chiamare un'API e accedere alle informazioni sull'utente.
    
- L'API risponde con i dati richiesti.

![[Pasted image 20241119171659.png]]
![[Pasted image 20241119171717.png]]
![[Pasted image 20241119171736.png]]
![[Pasted image 20241119171803.png]]
![[Pasted image 20241119171837.png]]
![[Pasted image 20241119171900.png]]
#### richiesta da parte di un browser

#### REFERENZE: