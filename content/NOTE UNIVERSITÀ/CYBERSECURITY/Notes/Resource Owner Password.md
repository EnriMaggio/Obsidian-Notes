#### Data: 19/11/2024 - 16:15

L'applicazione client è 
Consiste da parte dell'utente di fornire le credenziali spesso attraverso con un form interattivo

1. L'utente clicca su **Login** all'interno dell'applicazione e inserisce le proprie credenziali.
2. La tua applicazione inoltra le credenziali dell'utente al Authorization Server (all'endpoint `/oauth/token`).
3. Il **Auth0 Authorization Server** valida le credenziali.
4. Il **Auth0 Authorization Server** risponde con un **Access Token** (e opzionalmente con un **Refresh Token**).
5. La tua applicazione può utilizzare l'**Access Token** per chiamare un'API e accedere alle informazioni sull'utente.
6. L'API risponde con i dati richiesti.

![[Pasted image 20241119162133.png]]
![[Pasted image 20241119162309.png]]
![[Pasted image 20241119162448.png]]
![[Pasted image 20241119162552.png]]

#### REFERENZE: https://auth0.com/docs/get-started/authentication-and-authorization-flow/resource-owner-password-flow