Per simulare una camera reale abbiamo bisogno del mouse che si guarda intorno nelle scena ovvero cambia orientazione, mentre con la tastiera possiamo spostare la telecamera.

---
### Angoli di eulero

Gli angoli di Eulero sono un modo per rappresentare l’**orientamento** di un oggetto (nel nostro caso rotazioni in 3d) nello spazio tridimensionale usando **tre rotazioni** attorno agli assi principali (X, Y, Z), in una sequenza definita

L'orientamento di un oggetto nello spazio 3d può essere descritto da tre angoli

- **Pitch (beccheggio)** – rotazione intorno all’asse X (su e giù come alzare/abbassare la testa) controlla l’altezza dello sguardo.
- **Yaw (imbardata)** – rotazione intorno all’asse Y (destra o sinistra come un periscopio) controlla verso quale direzione "orizzontale" guarda la camera.
- **Roll (rollio)** – rotazione intorno all’asse Z (rotazione laterale, come inclinare la testa da un lato, come i player di rainbow six):  

![[Pasted image 20250512150747.png]]

Con la combinazione di queste tre angoli possiamo calcolare ogni vettore di rotazione in 3d. Nella maggior parte dei casi in grafica ci servono solo il pitch e lo yaw. Avendo questi due valori possiamo convertirli in un vettore che rappresenta un vettore direzione

---
### Conversione angoli eulero in vettore

sappiamo che

![[Pasted image 20250512150151.png]]

se l'ipotenusa è 1 riusciamo a trovare la lunghezza degli altri lati 
$$
cos(θ) = adiacente / ipotenusa` → `cos(θ) = x / 1 = x
$$
Ora provando ad immaginare il triangolo visto dall'alto con asse y fissato, il piano diventa XZ con il cateto adiacente ed opposto paralleli all'asse x e all'asse z

![[Pasted image 20250512151103.png]]

se applicassimo lo yaw stiamo ruotando la camera orizzontalmente (girare la testa destra e sinistra) in questo modo si cambia la direzione nel piano XZ, lo si trova con il cos relativo per asse X e con il sin per l'asse Z. Nell'immagine la camera si muoverebbe in senso antiorario

Sapendo l'angolo possiamo trovare il vettore direzione della camera


```cpp
glm::vec3 direction;
direction.x = cos(glm::radians(yaw)); // Note that we convert the angle to radians first
direction.z = sin(glm::radians(yaw));
```

(la componente dell' y corrisponderà al pitch)

La stessa cosa si può fare con il pitch guardando l'asse y come se fossimo seduti lungo l'asse XZ

![[Pasted image 20250512152149.png]]

Si può vedere che la direzione della componente y è uguale al sin(ptich) quindi l'aggiungiamo al vettore

```cpp
direction.y = sin(glm::radians(pitch));  
```

Ma siccome i lati XZ sono influenzati da cos(pitch) dobbiamo includerli nei componenti già presenti nel vettore

```cpp
direction.x = cos(glm::radians(yaw)) * cos(glm::radians(pitch));
direction.y = sin(glm::radians(pitch));
direction.z = sin(glm::radians(yaw)) * cos(glm::radians(pitch));
```

Infine otterremo il vettore finale di direzione dato il yaw e il pitch.

Siccome in opengl l'asse z che guarda la scena è negativa, dobbiamo sempre assegnare il yaw in negativo

---
### Collegamento con il mouse

i valori di yay e pitch si possono ottenere con il mouse, pensandoci:
- muovendo il mouse a sinistra a destra possiamo controllare lo yaw
- muovendo il mouse in altro a basso possiamo controllare il pitch

L'idea è quella di salvare la posizione del mouse nel frame precedente e calcolare nel frame attuale le nuove posizioni (cambiate), e la differenza tra questi due farà muovere il vettore direzione della camera