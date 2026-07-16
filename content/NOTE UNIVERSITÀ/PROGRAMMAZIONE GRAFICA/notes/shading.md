
---
### INTRO

Lo _shading_ non è altro che il calcolo del colore dei pixel secondo un certo metodo. Possiamo dire, ad esempio, che nella seguente immagine la teiera è di colore rosso:

![[Pasted image 20250523102631.png]]

Abbiamo applicato uno _shading_ basilare. Se invece cambiamo leggermente il metodo di _shading_, possiamo ottenere risultati più interessanti, come ad esempio:

![[Pasted image 20250523102729.png]]

Si possono notare alcuni parti più chiare e altre più scure dando un effetto tridimensionale. In questo caso possiamo dire che abbiamo applicato una luce sull’oggetto: essa appare in modo diverso in base al punto di applicazione della luce.  
Lo _shading_ non è altro che questo.

---
### COSA AVVIENE REALMENTE

immaginiamo di avere ora un piano immerso in una scena priva di luce, apparirà nero perchè non c'è illuminazione
![[Pasted image 20250523104008.png]]
Ora se applichiamo una luce vedremo il suo colore intrinseco
![[Pasted image 20250523104114.png]]
Possiamo utilizzare un vettore $\omega$ per indicare la direzione della luce applicato al centro del piano e diretto verso alla sorgente di luce.

Se adesso ruotiamo il piano (ad esempio attorno all’asse x) notiamo che il piano si scurisce progressivamente fino a quando diventa nero se la direzione si trova "dietro al piano"

![[Pasted image 20250523104430.png]]


---
### MATEMATICAMENTE COME COMPUTARE

immaginiamo di semplificare guardando da lato il tutto e con la luce che proietta un raggio su una parte di piano
![[Pasted image 20250523105257.png]]
è importante ora definire il vettore norma del piano, ovvero un vettore che è ortogonale al piano e in questo caso il vettore norma è uguale al vettore $\omega$ ma se iniziamo a ruotare il piano vediamo che i due vettori si distinguono per orientamento
![[Pasted image 20250523105719.png]]
se ruotiamo ancora di più notiamo che il raggio copre più area, questo vuol dire che se prima una certa quantità di luce si espandeva su un'area più piccola, adesso si espanderà su una area ancora più grande
![[Pasted image 20250523110111.png]]
E questo è il motivo per cui otteniamo meno luce per unità area. Quindi in base all'angolo tra la normale e $\omega$ cambierà l'intensità di luce sul piano 

Per computare questa cosa ci aiutiamo con la trigonometria.
se l'area dell superficie del piano eliminata era 1 ad esempio, l'area illuminata con il piano ruotato diventa maggiore e lo indichiamo con S, inoltre indichiamo con L la quantità di luce che arriva alla superficie
![[Pasted image 20250523111301.png]]
Quindi l'area illuminata dalla luce la si può indicare come $L/s$ significa che la luce si espande su S
![[Pasted image 20250523111604.png]]
Per computare $L/s$ prendiamo l'angolo che si forma con la normale e calcoliamo il coseno con le informazioni che già sappiamo e immaginiamo un triangolo
![[Pasted image 20250523112029.png]]

- **Il Triangolo Rettangolo:** L'immagine mostra un triangolo rettangolo formato dal raggio di luce, la normale alla superficie e la proiezione del raggio sulla superficie.
    
    - Il lato adiacente all'angolo θ è 1.
    - L'ipotenusa del triangolo è s.
    - L'angolo in alto a sinistra del triangolo è θ.
    - L'angolo tra l'ipotenusa s e il lato adiacente 1 è l'angolo formato dal raggio di luce con la superficie stessa. Questo angolo è π/2−θ (o 90∘−θ).
- **La relazione cosθ=1/s:**
    
    - Nel triangolo rettangolo, la definizione del coseno di un angolo è "cateto adiacente / ipotenusa".
    - In questo caso, per l'angolo θ:
        - Il cateto adiacente è la lunghezza "1".
        - L'ipotenusa è s.
    - Quindi, è corretto scrivere cosθ=1/s.
- **La relazione L/s=Lcosθ:**
    
    - Se riorganizziamo la formula precedente: s=1/cosθ.
    - Ora, se la quantità di luce che cade perpendicolarmente su un'unità di superficie è L (o se L è la quantità di luce che attraversa la larghezza "1"), allora quando la superficie è inclinata, la stessa quantità di luce L si distribuisce su una lunghezza maggiore s.
    - Quindi, la densità di luce (o la quantità di luce per unità di lunghezza in questo scenario 2D) sulla superficie inclinata sarà L/s.
    - Sostituendo s=1/cosθ in L/s: L/s=L/(1/cosθ)=L⋅cosθ.

L⋅cosθ ci dirà la quantità di luce che la superficie riceve

Abbiamo tre tipi di luci che possiamo implementare illuminando un oggetto

- [[Diffuse materiale lambertiano]]
- [[Specular]]
- [[ambient light]]

la formula per calcolare la luce diventa 
![[Pasted image 20250530100759.png]]

in opengl l'equazione storica è

![[Pasted image 20250530101410.png]]

esistono però diversi tipi di luce:
