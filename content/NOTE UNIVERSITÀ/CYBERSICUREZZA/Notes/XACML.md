#### Data: 03/12/2024 - 09:27

####  XACML(XML Access Control Markup Language)

E il fratello di SAML ed è una standard di [OASIS](https://it.wikipedia.org/wiki/XACML) per specificare le politiche di autorizzazione e diritti utilizzando la sintassi XML

Lo standard fornisce
- Linguaggio basato su XML per specificare politiche
- Risposta e richiesta basato su XML
- I tipi dei dati, funzioni, algoritmi combinatori 
- Architettura che definisce la componenti di rilievo in una implementazione
- Privacy dei profili
- RBAC profili

---
#### Architettura

![[Pasted image 20241203093602.png]]

l linguaggio XACML definisce due categorie di entità, entrambe definite da un **Uniform Resource Identifier**

- **Subject**: ovvero l'elemento che richiede l'accesso (es. Utenti, Computer, Servizi web...).
- **Resources**: cioè gli elementi a cui il Subject vuole accedere (es. File, Documenti, Database...).

Per svolgere la sua funzione, XACML ha bisogno di vari componenti logici che svolgono funzioni separate:

- **PEP**: il Policy Enforcement Point, il quale protegge una risorsa e ne permette l'accesso solo se la verifica di compatibilità con la policy è positiva.
- **PDP**: Policy Decision Point, il quale riceve tutti i vari parametri ed esamina la richiesta (Policy, Soggetto, Risorsa richiesta, Tipo di accesso, Contesto...) e decide se concedere o meno l'accesso in base alle politiche applicabili che ha ricercato. Presa la decisione, questa sarà comunicata al PEP.
- **PIP**: Policy Information Point, fornisce le informazioni(valori degli attributi) relative all'accesso richiesto.
- **PAP**: Policy Access Point, può creare le politiche di sicurezza e le salve nel repository, in seguito fornisce la policy applicabile all'accesso richiesto.

Nel dettaglio l'architettura contiene altri componenti di aiuto e di contorno

![[Pasted image 20241203095434.png]] 


---
#### Componenti fondamentali della struttura di XACML

![[Pasted image 20241203102005.png]]

- **Policy**
	consiste in una o un insieme di regole, in un algoritmo di conferma della regola e opzioni facoltative. E la base che serve al **PDP** per iniziare il suo processo
- **Policy set**
	è un gruppo (insieme) di politiche che possono essere localizzate in varie locazioni
- **Rule**
	è il componente basico della Policy, è quello che permette di fornire l'effetto desiderato della Policy. E un'espressione booleana che deve essere valutata
	![[Pasted image 20241203105005.png]]
- **Target**
	Specifica l'insieme delle richieste a cui applicare le Policy e Rule
	![[Pasted image 20241203105400.png]]
	Anyof elemento Or per gli elementi AllOf
	AllOf elemento And per gli elementi Match
	Match specifica una condizione sui soggetti, risorse e azioni

- **Attribute Designator**
	permette alla Policy di specificare un' attributo con un nome dato e un tipo e opzionalmente un emittente
- **Attribute Value**
	contiene letteralmente il valore
-  **Algoritmi di combinazione**
	sono delle procedure usati per riconciliare, unire i risultati di più valutazioni di varie Regole quando si star cercando di valutare una Policy, in un unica decisione 

Il diagramma seguente mostra il modello di policy XACML

![[Pasted image 20241203104042.png]]


---
#### Richesta XACML

![[Pasted image 20241203110940.png]]

la richiesta incapsula una richiesta di decisione per inviarla al PDP
#### Risposta XACML

![[Pasted image 20241203111426.png]]

Incapsula le decisioni di autorizzazione prodotte da PDP 
#### REFERENZE: https://it.wikipedia.org/wiki/XACML, https://dzone.com/articles/a-beginners-guide-to-xacml