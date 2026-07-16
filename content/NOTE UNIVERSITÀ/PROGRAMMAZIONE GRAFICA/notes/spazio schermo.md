Dallo spazio clip passiamo allo spazio schermo grazie alla trasformata viewport (o matrice di trasformazione) che trasforma coordinate da -1.0 a 1.0 a coordinate in un range definito da glViewPort, il risultato di queste coordinate verranno inviate al rasterizer per trasformarle in frammenti.

L'ultimo passo è la divisione prospettica che ci permette di passare dallo spazio 4d(coodinate omogenee) allo spazio 3d che poi viene disegnato su chermo

Si applica quindi una matrice di proiezione prospettica ad un vertice
$$
(x, y, z, w)
$$ che rappresentano coordinate nello spazio clip e la divisione prospettica divide ogni componente per la coordinate w, questo perchè ci permette di avere la profondità percepita 

- Quando un oggetto è lontano dalla telecamera, ha un valore di w più grande → x/w e y/w diventano più piccoli → l’oggetto sembra più piccolo.

- Quando è vicino alla telecamera, w è piccolo → x/w e y/w restano più grandi → l’oggetto sembra più grande.

Alla fine otteniamo coordinate in NDC

La matrice di proiezione può essere di due tipi
- __Proiezione Ortogonale__
	definisce un frustum con dimensioni cubiche che definisce lo spazio di clipping dove ogni vertice all'infuori di questa "scatola" viene tagliato fuori.
	Viene specificato per questa scatola la larghezza, lunghezza e la profondità che corrisponderà alla lunghezza del frustum visibile.

	![[Pasted image 20250508150915.png]]
	sono anche specificate un piano frontale e posteriore, ogni vertice che sta davanti al piano più vicino verrà tagliato fuori, ogni vertice che starà dietro al piano più lontano non verrà preso in considerazione.

	Tutte le coordinate che staranno dentro al frustum verrano mappate direttamente ai NDC senza nessun effetto secondario aggiuntivo, questo perché non verrà modificata la coordinata w del vettore trasformato, w è settato ad 1.0. Siccome mappa direttamente sullo schermo il risultato finale della immagine renderizzata non presenterà effetti di prospettiva o profondità degli oggetti

- __Proiezione Prospettica__
	La prospettiva in pratica ci permette di vedere gli oggetti più lontani come più piccoli, mentre gli oggetti più vicini come oggetti più grandi
	![[Pasted image 20250508152144.png]]
	Questo effetto viene raggiunto grazie alla matrice di proiezione prospettica che mappa un range di frustum ad un spazio clip, e manipola anche il valore di w per ogni coordinata di un vertice. I vertici più lontani avranno quindi una coordinata più grande rispetto ai vertici che si trovano più vicino al pov della camera
	![[Pasted image 20250508152702.png]] 
	Le coordinate in out vengono poi convertite in NDC
	La matrice di proiezione specifica vari parametri per determinare il suo frustum a cono
	![[Pasted image 20250508153054.png]] 
	- Fov: definisce il field of view