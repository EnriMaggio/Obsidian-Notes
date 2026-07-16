#### :LiCalendarClock:  28/10/2024 - 09:15

Se prima abbiamo approssimato sui dati, ora dobbiamo approssimare la semantica sul dominio di osservazione
#### Tracce semantiche

Le tracce delle semantiche di un programma la si può rappresentare con un grafico

![[Pasted image 20241028092329.png]]

- Ordinata: asse in cui ci sono i vari input del nostro programma
- Ascissa: rappresenta nel tempo, discretizza le tracce del programma fissando degli step di tempo che corrispondono ai cambi di stato delle tracce. Tra uno step e l'altro c'è quindi l'evoluzione dello stato della macchina

Una computazione è una traccia nel tempo che parte dall'instante 0 e forse finirà con l'andare nel tempo (ascisse), ed esistono infinite tracce da poter osservare(asse ordinata) perché ci sono infiniti input

La semantica di un programma la si può definire come un insieme infinito di tracce(sequenze) di stati (valori per x) potenzialmente infiniti

E per questi due motivi dobbiamo approssimare

#### Come approssimiamo

Teniamo conto che astrarre questa volta non può evitare la non terminazione, ovviamente cerchiamo di raggiungere la decidibilità

![[Pasted image 20241028093438.png]]

Quindi l'idea è quella di non guardare più gli singoli stati, ma insiemi di essi potenzialmente infiniti in una singola traccia, non più tutte

Il calcolo su questi insiemi avviene per punto fisso. Il processo parte da un insieme di stati iniziali e nello scorrere del tempo andremo a collezionare tutti gli stati raggiunti in ogni passo di esecuzione (Reachability semantics)

Facendo questo abbiamo una perdita di informazioni riguardante la posizione degli stati raggiunti di una specifica traccia (visto che ora ne abbiamo una)

![[Pasted image 20241028094548.png]]
![[Pasted image 20241028094636.png]]

Per questa approssimazione dovremmo considerare tutte le tracce disponibili tra gli insieme di stati, vengono dette tracce spurie aggiungendo di fatto errore

#### Collecting semantics

Nel tempo discreto ad ogni passo di computazione verrà eseguita un'istruzione del programma e possiamo collezionare gli stati ma stavolta per punto di programma, non si guarderà più il tempo di esecuzione

![[Pasted image 20241028095751.png]]
![[Pasted image 20241028100946.png]]

Questo però non è ancora decidibile perché siamo ancora nel mondo concreto (stiamo guardando tutti i possibili stati). L'unica cosa che può far intuire alla decibilità è la stabilizzazione degli insiemi di stati ovvero vedere se non cambiano.

Per risolvere a questo punto dobbiamo andare a considerare le proprietà invariante sui stati raggiungibili, di fatto aggiungendo più rumore.

Ad esempio come proprietà si possono vedere gli intervalli

![[Pasted image 20241028102043.png]]
![[Pasted image 20241028102132.png]]

Ricapitolando in un primo momento abbiamo collezionato gli stati e in un secondo momento abbiamo computato il punto fisso sulla proprietà degli stati raggiungibili

![[Pasted image 20241028102803.png]]

Più in generale (di default)

![[Pasted image 20241028102907.png]]

#### Semantica Collecting semantics

![[Pasted image 20241028103534.png]]
![[Pasted image 20241028103549.png]]

#### :LiExternalLink: REFERENZE: