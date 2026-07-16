per costruire questa matrice dobbiamo proiettare ogni oggetto sul piano vicino del frustum

![[Pasted image 20250508215755.png]]

come si vede nell'immagine prendiamo ad esempio un punto bianco che sta dentro al frustum, dalla telecamera fino al punto c'è una linea che li collega e che attraversa il near panel, nel preciso punto in cui interseca quella linea, quello sarà la posizione del punto bianco proiettato sul near panel che sarà da renderizzare nell'immagine, siccome i punti devono essere compresi tra -1.0 e 1.0, il near panel usa gli stessi range.

Prima di trovare i punti proiettati con la trigonometria, dobbiamo capire il discordo del FOV

![[Pasted image 20250508220953.png]]

piano più vicino deve essere compreso tra -1.0 e 1.0 (nell'asse della y) per rispettare il rasterizer, ma possiamo spostare il piano nell'asse z più vicina o lontana rispetto alla posizione della telecamera, a seconda di come spostiamo il piano frontale, il piano sopra e sotto formano un angolo di 90 gradi (45 gradi + 45 gradi)con l'asse z, questo angolo viene chiamato fov verticale

Se allontanassimo il piano frontale dalla camera il fov diminuisce

![[Pasted image 20250508221800.png]]

Se cambiasse solo il fov e non il resto, la vista verticale si riducerebbe e mapperemo molti meno punti dello spazio 3d, infine i punti degli oggetti proiettati sul piano frontale verranno percepiti come più grandi. In pratica abbiamo fatto uno zoom in.

Al contrario se spostassimo il piano frontale più vicino alla camera il fov aumenta, ovvero angolo più grande, quindi riuscirò a mappare e a proiettare più oggetti ma appareranno più piccoli, quindi si sarà fatto uno zoom out

![[Pasted image 20250508222438.png]]

Per trovare il punto proiettato sul piano frontale dobbiamo usufruire di un po' di trigonometria

![[Pasted image 20250508224959.png]]

L'angolo è diviso in due parti uguali, e possiamo definire d come la distanza dall'origine a dove è situato il pannello frontale. Con questo si può immaginare un triangolo tra d, angolo e cateto opposto che sarà sempre 1 (per il rasterizer)

Detto questo riusciamo a trovare d ricavandolo dalla formula della tangente di un angolo che equivale al rapporto tra la misura del lato opposto (1, quello tra d e riga arancione) e lato adiacente (ovvero d). Siccome abbiamo i restanti ingredienti possiamo esplicitare d e avere la formula per trovarlo

![[Pasted image 20250508230644.png]]

il punto rosso è quello da proiettare e il punto verde è quello proiettato, in questo momento x non ci interessa, yp è il punto da trovare e d lo sappiamo. Si può notare che si formano due triangoli simili (tra origine,punto verde e  d e tra origine,punto rosso e asse z).

Siccome yp è la proiezione di y, allora si può applicare la proporzione tra i lati opposto di entrambi i triangoli (yp / d e y/z), se i triangoli sono simili allora il loro rapporto è uguale, dopo possiamo esplicitare yp e sappiamo anche d, sostituendo nella formula riusciamo finalmente a trovare yp

Nel fov orrizontale(vista da sopra) la formula è analoga, basta usare x.

Queste operazioni ovviamente un costo quindi adesso possiamo costruire la matrice che contiene la trasformazione della vista

![[Pasted image 20250508232851.png]]

x ed y rimangono comunque e sono pesantuccie, si copia il valore di z nella coordinata w

![[Pasted image 20250508233540.png]]

Questa matrice non tiene conto dell'aspect ratio, ovvero indica il rapporto fra le due dimensioni x e y (larghezza e altezza di un'immagine)

![[Pasted image 20250509085043.png]]

Il passaggio fondamentale è quello di matchare il rasterizer con l' aspect ratio della finestra

![[Pasted image 20250509085300.png]]![[Pasted image 20250509085453.png]]

Il rasterizer che è un passaggio intermedio tra trasformazioni 3d e immagine in output, deve applicare una trasformata viewport per spostare i pixel renderizzati in un quadrato tra -1.0 e 1.0 alla griglia dello schermo dove vedremo l'immagine di output

![[Pasted image 20250509090052.png]]

L'idea è quella di proiettare i punti dello schermo sul quadrato del rasterizer semplicemente dividendo per il punto l'aspect ratio.

Un altro passo da fare è che i pannelli di clip frontale e posteriore sono normalizzati anch'essi (per il discorso del [[Depth Buffer]]) 

![[Pasted image 20250509092009.png]]

Come faccio ad inserire nella matrice questa nuova informazione. In generale

![[Pasted image 20250509092307.png]]

La terza riga che corrisponde alla coordinata z, x e y non contribuiscono e quindi possiamo settarli a 0, quindi z sarà

![[Pasted image 20250509092445.png]]
(successivamente dobbiamo fare anche la divisione prospettica)

Ora la Z la possiamo sostituire sia con Near e Far originariamente specificati e porli ad eguagliare rispettivamente a -1 e 1
![[Pasted image 20250509092712.png]]
Notiamo che possiamo estrarre A nella prima equazione e sostituirla nella seconda

![[Pasted image 20250509092924.png]]
Portando -1 a destra si somma con l'altro 1 e a sinistra si fa il minimo comune denominatore

![[Pasted image 20250509093101.png]]
raccogliamo per B e di seguito lo esplicitiamo

![[Pasted image 20250509093315.png]]
questo B appena trovato la sostituiamo nella A iniziale

![[Pasted image 20250509093433.png]]
NearZ si cancellano tra di loro e se proseguiamo con i conti otteniamo

![[Pasted image 20250509093628.png]]

Alla fine siamo riusciti a trovare le equazione per A e per B

![[Pasted image 20250509093907.png]]

Sostituendoli alla fine della matrice otteniamo

![[Pasted image 20250509093939.png]]