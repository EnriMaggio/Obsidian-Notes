#### Data: 19/11/2024 - 15:51

Il flusso di autorizzazione inizia con in client che reindirizza l'utente all'endpoint /authorize

L'applicazione client ha un frontend e backend
![[Pasted image 20241119155300.png]]
![[Pasted image 20241119155515.png]]

Se risposta è avvenuta con successo allora nel campo CODE ci sarà l'effettivo codice di autorizzazione. L'applicazione ora può usare il codice per fare richiesta di accesso al token per la risorsa voluta
![[Pasted image 20241119155943.png]]
![[Pasted image 20241119160232.png]]
![[Pasted image 20250227192621.png]]
![[Pasted image 20241119160528.png]]

#### REFERENZE: https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-auth-code-flow