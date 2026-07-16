
Una scheda grafica (detta anche scheda video o unità di elaborazione grafica) è un componente hardware che elabora le informazioni grafiche e le trasforma in segnali visivi da inviare al monitor del computer, consentendo la visualizzazione di immagini, video e animazioni

le schede grafiche sono specializzate negli applicativi grafici, questo perchè sono abilitate al calcolo parallelo e possono permettersi migliaia di thread concorrenti in esecuzioni, quindi forti nei calcoli paralleli e riescono a "colorare" più pixel alla volta

il processo in pratica è quello di usare i componenti hardware per renderizzare velocemente oggetti 3d in pixel sullo schermo del computer attraverso architetture hardware

Bisogna però dire cosa fanno queste gpu, infatti sono programmabili attraverso librerie grafiche e possono avere controllo su
- geometria processata
- vertici
- frammenti

i frammenti (detti anche fragments) sono praticamente i pixel disegnati che devono avere ancora il colore

---
### cpu e gpu

la gpu comunque resta sotto comando della cpu e bisogna distinguerle
- *host:* componenti cpu dell'applicazione
- *device:* è la parte gpu dell'applicazione grafica, include i dati e la computazione che sono salvati ed eseguiti sulla gpu

Tutti i programmi che utilizzano hardware grafico devono per forza prima stabilire un mapping tra memoria cpu e gpu, in pratica si parte sempre dalla cpu che dialogarà con la gpu

---
### contesto grafico

Un contesto grafico (o "ambiente grafico") si riferisce all'interfaccia utente di un sistema operativo che permette di interagire con il computer tramite oggetti grafici come icone e finestre, anziché comandi testuali.

il contesto grafico comprende
- sistema operativo
- driver hardware
- sistema di finestre

il contesto è stabilito spesso con chiamate API al sistema di finestre

---
### OpenGL

OpenGL è una specifica API (interfaccia di programmazione delle applicazioni) per la grafica 2D e 3D accelerata via hardware, che consente agli sviluppatori di creare applicazioni con grafica di alta qualità su diverse piattaforme e linguaggi di programmazione. È multipiattaforma



opengl cambia lo stato dell'hardware grafico e può essere usato per
- dichiarare e definire geometria
- caricare vertex shader
- caricare fragmente shader
- determinare come la computazione occorre in base ai dati che attraversano l'hw

opengl gestisce solo la pipeline grafica e il codice scritto riguarda la cpu e la gpu. E descritto nel seguente modo

![[Pasted image 20250904150640.png]]

---
### buffer

i buffer sono locazioni lineari di memoria nel dispositivo che contengono dei dati come
- geometria
- texture
- immagini piane

La cpu scrive direttamente su questi buffer e la gpu opererà sui buffer che conterranno questi dati

Alla fine della pipeline grafica, il set finale di pixel colorati possono essere linkate ai display
i dati associati questi pixel sono generalmente degli array a due dimensioni con i colori come valori

intrinsicamente il dato è 2D, ma è rappresentato efficientemente nella gpu come un array ad una dimensione, questo array quindi implementa un display buffer che eventualmente verrà mappata alla finestra

Alla fine della rasterizzazione, il processo dei frammento e i blendig stages scrivono dati nell'output del display buffer memory

molte applicazioni preferiscono uno schermo con doppio buffer uno front e uno back
quello front conterrà i colori che devono essere visualizzati attualmente e il back viene utilizzato per i colori che dovranno essere aggiornati

al fine del rendering loop i buffer vengono swappati con un cambio di puntatori e il sistema di finestre gestirà il contenuto con il buffer più aggiornato

---
### stati

le schede grafiche mantengono i stati computazionali che determinano come le compuatazioni associate alle scene di dati e shader occorrono nel hardware grafico

Opengl è di per se una macchina a stati molto grande, infatti sono una collezione di variabili che defincono come opengl opera. 

Lo stato di opengl si chiama contesto di opengl



---
### shaders

rappresentano il meccanismo di come le computazioni occorrono nella gpu e sono di fatto programmi eseguiti in parallelo nella gpu e sono scritti in GLSL. opengl compila questi programmi (li tratta come stringa).

- *vertex shader:*
	Il vertex shader è un componente programmabile della pipeline grafica che manipola i dati di ogni vertice di un modello 3D, modificandone la posizione, la rotazione, la scalatura e le proprietà geometriche per trasformare la geometria nella vista 3D. Operando su singoli vertici senza conoscere i loro vicini, il suo scopo principale è di trasformare le coordinate dei vertici prima che vengano elaborate dai successivi shader e dal rendering finale. 
- *fragment shader:*
	Il fragment shader (o pixel shader) è un programma che, all'interno di un'unità di elaborazione grafica (GPU), determina il colore e l'aspetto finale di ogni singolo pixel sullo schermo. Inserisce dettagli come l'illuminazione, le texture, le ombre e altri effetti visivi, campionando le texture attraverso le coordinate interpolate per creare immagini realistiche e coinvolgenti per videogiochi e applicazioni grafiche. 