
come già menzionato in precedenza, gli shader sono piccoli programmi che restano in gpu e trasformano semplicemente input in output. Gli shader codificano un insieme di istruzioni che sono tutte eseguite in una volta per ogni singolo vertice o singolo pixel

è uno dei motivi per cui abbiamo le gpu, piuttosto di avere un potente microprocessore che fa le cosa una alla volta, è meglio avere tanti piccoli microprocessori che lavorano in parallelo nello stesso momento

![[Pasted image 20250905093154.png]]

una loro caratteristica è che sono programmi isolati, non comunicano tra di loro, quindi devono passarsi variabili di input e output.

Avendo questa caratteristica purtroppo non si ha nessun controllo e nessuna vista sui thread paralleli, ogni thread è cieco e senza memoria agli altri thread


---
### GLSL

gli shader sono scritti in un linguaggio c-like che si chiama glsl, è pensato in modo da gestire facilmente vettori e matrici.

negli shader sono presenti quindi
- numero versione
- variabili di input in
- variabili di output out
- variabili uniform
- funzione main
![[Pasted image 20250905095916.png]]


---
### tipi di dati glsl

![[Pasted image 20250905100315.png]]i componenti di un vettore x ad esempio possono essere accessi con x.x, x.y, x.z
glsl è in grado di usare i colori rgba o stpq per le coordinate texture


---
### funzionamento variabili

gli shader specificano gli input e gli outputs utilizzando le keywords in e out, se si vuole passare informazioni tra gli shader (unico modo che hanno per comunicare) il nome della variabili out dello shader che vuole passare ad un secondo shader, quest'ultimo deve avere lo stesso nome della variabile ma con keyword in.

![[Pasted image 20250905101238.png]]

Quando i nomi sono uguali OpenGL linka queste variabili insieme 

il vertex shader ha come obbligo gli attributi dei vertici (che arrivano direttamente dai vertex data) come variabili in. Per definire come è organizzato il vertex data, si specificano gli input con il metadato _location_, così metchano con la configurazione degli attributi nella cpu.

Il fragment shader ha come obbligo invece di avere in output un vec4 color, siccome questo shader deve generare il coloro del pixel finale


---
### funzionamento uniform

gli uniform sono un altro modo di passare dei dati nella nostra applicazione dalla cpu alla gpu. Gli uniform sono quindi globali, sono unici per gli programmi oggetto shader. Ogni shader può accedere agli uniform in qualsiasi stage.

Essendo globali gli uniform possono cambiare il loro valore 

per usare una uniform dobbiamo utilizzare nel render loop all'interno del main la funzione glGetUniformLocation
![[Pasted image 20250905111944.png]]