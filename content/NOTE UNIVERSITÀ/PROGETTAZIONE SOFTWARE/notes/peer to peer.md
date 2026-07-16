rappresenta un modello decentralizzato che si distingue nettamente dalle architetture gerarchiche o centralizzate.

![[Pasted image 20260117155615.png]]

La caratteristica fondamentale del pattern Peer-to-Peer è:

- l'assenza di una distinzione rigida tra fornitori e consumatori di servizi.
-  **Ruoli Simultanei:** Ogni componente (peer) del sistema agisce **contemporaneamente sia da client che da server**.
- **Interfacce:** Ogni peer espone un'interfaccia che specifica sia i servizi offerti (ruolo server) sia i servizi richiesti agli altri nodi (ruolo client)
- ogni nodo può comunicare con tutti gli altri nodi della rete
- i nodi sono altamente intercambiabili, se un nodo per qualche motivo non riesce a fornire un certo servizio, magari un altro nodo disponibile può fornire quello stesso servizio
- conservazione degli stessi dati tra più peer

Un esempio di architettura peer to peer è il protocollo bittorrent
![[Pasted image 20260117155953.png]]
ad esempio il tracker contiene la lista dei peer, I file sono divisi in chunks, e questi chunks vengono distribuiti sui peers

**Vantaggi**

- **Scalabilità:** I sistemi P2P "scalano molto bene", poiché l'aggiunta di nuovi nodi aumenta sia la domanda che l'offerta di risorse.
- **Tolleranza ai guasti (Fault Tolerance):** Il sistema è molto robusto. Poiché non esiste un server centrale critico, il guasto di un singolo nodo non compromette l'intera rete.
- **Replicazione dei Dati:** I dati possono essere replicati su molti peer. Di conseguenza, se un peer si disconnette, le informazioni non vengono perse poiché esistono copie ridondanti altrove.