L’identificazione dei rischi è un processo essenziale che si basa sull’uso di liste di controllo specifiche per ciascuna categoria di progetto, al fine di personalizzare l’approccio al contesto specifico del progetto. Queste liste sono importanti per identificare i rischi potenziali associati alle diverse categorie di requisiti.

Si possono identificare i rischi andando a controllare componente per componente nel nostro sistem to-be e domandarsi se potrebbero fallire e in caso come,perchè e quali sono le possibili consequenze

si utilizzano degli alberi per aiutarci a mappare rischi o fallimenti e le relative cause, ed è composto da 

- nodi che descrivono il fallimento
- nodi foglia che indicano fallimenti elementari che non si possono raffinare
- link and/or 


![[Pasted image 20250605173414.png]]

Ci sono delle linee guida per identificare i rischi leggendo gli statement che si stanno scrivendo nella ingegneria dei requisiti

ad esempio basato sulle **Guidewords** che aiutano a identificare problemi sistematici attraverso pattern linguistici comuni:

- **NO**: "Qualcosa manca"
- **MORE**: "Ci sono più cose del previsto"
- **LESS**: "Ci sono meno cose del previsto"
- **BEFORE**: "Qualcosa accade prima del previsto"
- **AFTER**: "Qualcosa accade dopo del previsto"

I problemi reali derivano spesso da **combinazioni** di eventi/condizioni di fallimento di base.

Quando si ha un risk tree si possono identificare dei cut set, è la minima combinazione di and dei fogli dell'albero che fanno scattare il rischio che si ha nel nodo root

Per identificare i cut set si deve partire dal nodo radice e in seguito scendere 

![[Pasted image 20250605174754.png]]

Per identificare i rischi, oltre a queste analisi, posso dotarmi di scenari, perchè aiutano nella formulazione delle domande WHAT-IF

e chiedendo agli stakeholder (con tecniche di elicitazione), sessioni di gruppo e il riuso della conoscenza sulla base di esperienze passate.
