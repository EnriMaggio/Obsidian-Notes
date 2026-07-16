Per ridurre l’intensità della luce in base alla distanza percorsa da un raggio luminoso, si utilizza generalmente un meccanismo chiamato **attenuazione**.  
Un modo semplice per ridurre l’intensità luminosa sulla distanza è usare un’equazione **lineare**.  
Un’equazione lineare riduce l’intensità in modo proporzionale alla distanza, facendo in modo che gli oggetti più lontani appaiano meno illuminati. Tuttavia, una funzione lineare **tende a sembrare poco realistica**.  
Nel mondo reale, una sorgente luminosa è **molto intensa da vicino**, ma **l’intensità cala rapidamente** con la distanza; la luce rimanente **diminuisce più lentamente** man mano che ci si allontana.

Abbiamo quindi bisogno di un’equazione diversa per rappresentare meglio la **riduzione dell’intensità della luce**.

La formula seguente calcola un **valore di attenuazione** basato sulla **distanza tra il frammento (punto della superficie) e la sorgente luminosa**, che poi viene **moltiplicato per il vettore di intensità della luce**:

$$
Fatt= \frac{1.0}{K_c + K_l \cdot d + K_q \cdot d^2}​
$$
Dove:
- $d$ è la distanza tra il frammento e la sorgente di luce
    
- $Kc$​, $Kl$​ e $Kq$ sono **termini configurabili**:

- **Termine costante** $Kc$​:  
    Di solito si imposta a **1.0**, per evitare che il denominatore diventi troppo piccolo (che causerebbe un'intensità artificiosamente alta, cosa che vogliamo evitare).
    
- **Termine lineare** $Kl$​:  
    Viene **moltiplicato per la distanza**, e riduce l’intensità in modo **lineare**.
    
- **Termine quadratico** $Kq$​:  
    Viene **moltiplicato per il quadrato della distanza**.  
    Questo introduce una **riduzione quadratica** dell’intensità.  
    Quando la distanza è piccola, questo termine ha poco peso rispetto al lineare, ma **cresce rapidamente** all’aumentare della distanza.
    

la luce **diminuisce in modo quasi lineare** inizialmente, finché la distanza non è abbastanza grande da far **dominare il termine quadratico**, provocando un calo molto più rapido dell’intensità.  
L’effetto risultante è che la luce è **molto intensa da vicino**, **si attenua rapidamente** con la distanza, e infine **decresce più lentamente** man mano che ci si allontana ulteriormente.

![[Pasted image 20250530113906.png]]
Il grafico mostra l’andamento dell’intensità su una distanza di 100: si nota che la luce è massima quando la distanza è minima, ma appena si allontana, l’intensità **si riduce drasticamente**, tendendo poi gradualmente a **zero** attorno alla distanza 100.