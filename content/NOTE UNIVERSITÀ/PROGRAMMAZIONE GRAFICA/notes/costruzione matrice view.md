con la matrice view andremo a creare la nostra camera nella scena 3d e trasforma il sistema di riferimento mondo nel sistema di riferimento camera.

Per costruire una camera abbiamo bisogno di
- posizione di essa nello spazio mondo
- la direzione di dove sta guardando
- un vettore che punta a destra dalla camera
- un vettore che punta in alto dalla camera

![[Pasted image 20250510175644.png]]

L'intento è quello ci piazzare la camera all'origine e quindi di spostare gli oggetti relativamente alla camera del sistema e che stia guardando verso l'asse z in negativo


Per costruire la camera dobbiamo trovare i 3 assi x,y,z che partono dalla posizione della camera, si utilizza un modello chiamato UVN e presenta due attributi
- locazione della camera
- gli assi del modello UVN

![[Pasted image 20250510173625.png]]

gli assi sono uguali descritti prima con
- N che guarda la scena (z-)
- U che guarda a destra (x+) che corrisponde al sistema di coordinate standard
- V che guarda in alto (y+) che corrisponde al sistema di coordinate standard

Da notare che ogni asse è ortogonale rispetto agli altri, quindi formano 90 gradi, questo è utile perchè ci permette di trovare gli assi con il cross product. Questi assi sono linearmente indipendenti.

Questi assi una volta trovati vanno normalizzati (lunghezza = 1)


---
### asse z
per trovare la direzione a cui sta puntando, assumendo che la posizione della camera sia 0, dobbiamo sottrarre il vettore posizione della camera con il vettore origine della scena (ovvero il target, dove vogliamo guardare) siccome in opengl la z negativo è quella che guarda 

Supponiamo che:
- La **posizione della camera** sia un vettore: `cameraPos`
- Il punto che sta guardando sia l’origine della scena: `(0, 0, 0)`

Se si fa:
$$
direction=target−cameraPos
$$ 
in questo caso:

$$
direction=(0,0,0)−cameraPos
$$ 
il risultato da un vettore che **punta dalla camera verso il centro della scena**.

In opengl però si scambia l'ordine degli operandi, questo perchè si usa il right hand system, e l'asse z negativo è dove in teoria la camera guarda, quindi dobbiamo invertire la sottrazione in modo che l'asse z sia positivo per la matrice view

Quindi, per rispettare questa convenzione, invece che usare:
$$
target−cameraPos
$$

si inverte l’ordine:
$$
cameraPos−target
$$

---
### asse x

ora dobbiamo trovare l'asse x positivo della camera, per farlo ci serve prima un vettore up che punta in alto nello spazio mondo, poi si esegue un prodotto vettoriale tra questo nuovo vettore e il vettore direzione, il risultato sarà l'asse x che sarà ortogonale agli altri due assi e che punta dove vogliamo, se volessimo che punta verso l'asse x negativo basta scambiare l'ordine dei due vettori

---
### asse y

ora siccome che abbiamo il vettore direzione che punta verso l'asse z positivo e anche l'asse x positivo, basta fare il prodotto vettoriale tra questi due assi e si trova l'ultimo asse 

![[Pasted image 20250510182958.png]]
![[Pasted image 20250510183051.png]]

Non è ancora finita ma ci manca poco

Siccome abbiamo tre vettori che specificano un sistema di riferimento, possiamo creare una matrice Look At che ospita questi vettori insieme ad un vettore di traslazione negato per la camera. Così ogni coordinata dello spazio mondo verrà trasformato nel nuovo sistema di riferimento. È come se spostassimo il mondo relativamente davanti alla camera, piuttosto che la camera che si muove

![[Pasted image 20250510183754.png]]

Come spiegato prima
- **Right (R)** → l'asse +X della camera
- **Up (U)** → l'asse +Y della camera
- **Direction (D)** → l'asse **-Z** della camera (la camera "guarda" lungo `-Z`)

Questi tre vettori formano la base della nuova coordinata (spazio camera)
Il vettore di traslazione è negato perchè vogliamo spostare il mondo nella direzione opposta alla posizione della camera