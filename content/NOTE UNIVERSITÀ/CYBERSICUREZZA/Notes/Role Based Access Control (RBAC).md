#### Data: 26/11/2024 - 11:12

è un meccanismo di controllo degli accessi che definisce ruoli e privilegi per determinare se un utente deve essere autorizzato ad accedere a una risorsa. I ruoli sono definiti in base a caratteristiche quali la posizione, il reparto, l'anzianità o le mansioni dell'utente.

Ad un ruolo creato, verranno associati dei privilegi e diritti per accedere ad alcune risorse, infine questi ruoli vengono assegnati agli utenti
#### Regole principali del sistema RBAC

1. **Assegnazione del ruolo:** a un utente devono essere assegnati uno o più ruoli attivi per esercitare autorizzazioni o privilegi.  
      
2. **Autorizzazione del ruolo:** l'utente deve essere autorizzato ad assumere il ruolo o i ruoli che gli sono stati assegnati.  
      
3. **Autorizzazione:** le autorizzazioni o i privilegi vengono concessi solo agli utenti autorizzati tramite l'assegnazione dei ruoli.

## Vantaggi RBAC
### 1. **Semplificazione della gestione degli accessi**

- Gli utenti non ricevono permessi individuali, ma vengono assegnati a ruoli con permessi predefiniti. Questo riduce la complessità nella configurazione e manutenzione degli accessi.
- È più facile aggiungere o rimuovere utenti da un ruolo rispetto a gestire singoli permessi.

### 2. **Maggiore sicurezza**

- Gli utenti hanno accesso solo alle risorse necessarie per il loro ruolo, limitando i rischi derivanti da accessi non autorizzati.
- La gestione centralizzata dei ruoli aiuta a evitare che i permessi siano concessi arbitrariamente.

### 3. **Facile scalabilità**

- In ambienti con molti utenti, RBAC semplifica l'aggiunta di nuovi utenti o la modifica dei permessi. Basta aggiornare il ruolo, e i cambiamenti si rifletteranno automaticamente su tutti gli utenti assegnati a quel ruolo.
- Ideale per organizzazioni di grandi dimensioni o con dipendenti distribuiti su diverse sedi.

### 4. **Riduzione degli errori**

- Le politiche basate sui ruoli sono più chiare e facili da implementare, riducendo il rischio di errori nella configurazione degli accessi.
- Gli amministratori non devono gestire permessi individuali utente per utente.

### 5. **Conformità e audit semplificati**

- Con RBAC, è più semplice dimostrare che gli accessi rispettano i requisiti normativi e di sicurezza. I ruoli possono essere progettati per allinearsi a regole di conformità.
- I log di accesso e l'assegnazione dei ruoli rendono gli audit più veloci ed efficienti.

### 6. **Flessibilità**

- I ruoli possono essere definiti per coprire un'ampia varietà di esigenze organizzative, dai dipartimenti ai progetti specifici.
- RBAC può essere adattato per supportare modelli avanzati come il _Least Privilege_ (assegnare il minimo necessario di permessi).

### 7. **Migliore produttività per gli utenti**

- Gli utenti ricevono i permessi giusti senza dover richiedere e attendere autorizzazioni manuali.
- I nuovi membri del team possono iniziare a lavorare immediatamente una volta assegnati al ruolo corretto.

In sintesi, **RBAC** rende la gestione degli accessi più **efficiente**, **sicura**, e **adatta a organizzazioni complesse** o in rapida crescita.


Nonostante questo RBAC è molto difficile da implementare correttamente, soprattutto quando si hanno tanti utenti e quindi ruoli 
#### Famiglia RBAC

![[Pasted image 20241126113238.png]]
![[Pasted image 20241126113403.png]]

Nelle gerarchie invece chi sta sotto ai padri, eredita certi permessi ma non tutti 
![[Pasted image 20241126113624.png]]
![[Pasted image 20241126114315.png]]

La separazione dei doveri può essere statica o dinamica:
![[Pasted image 20241126114935.png]]



#### REFERENZE: https://www.entrust.com/it/resources/learn/what-is-role-based-access-control