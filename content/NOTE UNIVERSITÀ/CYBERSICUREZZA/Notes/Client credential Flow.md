#### Data: 19/11/2024 - 16:55

Questo flusso invece consiste che un'applicazione scambia le sue credenziali di applicazione per un token di accesso

1. L'applicazione invia le credenziali dell'applicazione al **Authorization Server**. Per ulteriori informazioni sui metodi di autenticazione del client, consulta **Application Credentials**.
2. Il **Authorization Server** valida le credenziali dell'applicazione.
3. Il **Authorization Server** risponde con un **Access Token**.
4. L'applicazione può utilizzare l'**Access Token** per chiamare un'API per conto di se stessa. Per ulteriori dettagli su questo processo, consulta **Validate JSON Web Tokens**.
5. L'API risponde con i dati richiesti.

![[Pasted image 20241119170235.png]]
![[Pasted image 20241119170125.png]]
![[Pasted image 20241119170055.png]]
![[Pasted image 20241119170153.png]]
#### REFERENZE: https://auth0.com/docs/get-started/authentication-and-authorization-flow/client-credentials-flow