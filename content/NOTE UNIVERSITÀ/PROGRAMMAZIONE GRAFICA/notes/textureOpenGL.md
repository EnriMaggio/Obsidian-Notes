la [[Texture]] da illusione ad un oggetto 3d di essere dettagliato senza specificare tanti vertici.
se prendessimo ad esempio questa texture

![[Pasted image 20250905163255.png]]
e l'applicassimo ad un triangolo, risulta questo

![[Pasted image 20250905163133.png]]


---
### coordinate texture

per mappare una texture ad un triangolo dobbiamo fare in modo di dire ad ogni vertice del triangolo quale parte della texture corrisponde.

Quindi ogni vertice deve salvarsi oltre alla sua posizione, le coordinate texture che fanno riferimento a quale parte della texture fanno riferimento, per i frammenti all'interno della triangolo ci pensa l'interpolazione.

le coordinate texture vanno da un intervallo tra 0.0 e 1.1 negli assi x e y, siccome le texture sono immagini 2D e sono rappresentate da pixel che hanno coordinate.

0.0 è il punto di origine della texture in basso a sinistra e la fine è 1.1 in alto a destra

![[Pasted image 20250905163948.png]]

per un triangolo basta specificare la coordinata (0.0, 0.0) per il vertice in basso a sinistra e così via
```cpp
float vertices[] = {
    -0.5f, -0.5f, 0.0f, // angolo basso sinistra  
     0.5f, -0.5f, 0.0f, // angolo basso destra
     0.0f,  0.5f, 0.0f  // angolo centro alto
};  

float texCoords[] = {
    0.0f, 0.0f,  // angolo basso sinistra  
    1.0f, 0.0f,  // angolo basso destra
    0.5f, 1.0f   // angolo centro alto
};
```

il processo che recupera il colore dalla texture usando le coordinate texture viene chiamato sampling 

---
### texture wrapping

se specificassimo coordinate texutre al di fuori dell'intervallo (0,0) (1,1) opengl offre diversi comportamenti di wrapping per corregere e ripetere la texture

![[Pasted image 20250905165254.png]]

![[Pasted image 20250905165302.png]]

queste opzioni possono essere settate nella funzione glTexParameter

```cpp
glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_MIRRORED_REPEAT);
glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_T, GL_MIRRORED_REPEAT);
```
- primo argomento specifica la texture target di cui sta trattando
- il secondo parametro indica l'asse in considerazione
- il terzo parametro setta il metodo di wrapping

---
### texture filtering

le coordinate texture non dipendo dalla risoluzione della texture, sono solo valori float, quindi opengl deve decidere quale pixel della texture (texel) assegnare a quella coordinate texture.

Può capitare di avere oggetti tanto grandi e avere risoluzioni delle texture basse e OpenGL offre opzioni di texture filtering

- GL_NEAREST
	seleziona il texel il cui centro è più vicino alla coordinata della texture. Qui sotto potete vedere 4 pixel in cui la croce rappresenta le coordinate esatte della texture. Il texel in alto a sinistra ha il centro più vicino alla coordinata della texture e viene quindi scelto come colore campionato
	![[Pasted image 20250905170550.png]]
- GL_LINEAR
	prende un valore interpolato dai texel adiacenti alla coordinata della texture, approssimando un colore tra i texel. Minore è la distanza tra la coordinata della texture e il centro di un texel, maggiore è il contributo del colore di quel texel al colore campionato. Di seguito possiamo vedere che viene restituito un colore misto dei pixel adiacenti:
	![[Pasted image 20250905170641.png]]

![[Pasted image 20250905170756.png]]

si possono specificare la maggiorazione e minorazione quando si upscala o downscala

```cpp
glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_NEAREST); glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR);
```


---
### mipmap

le mipmap servono per correggere il problema di artefatti da parte di texture ad alta risoluzione che sono applicati a degli oggetti nella scena che sono piccoli (m(agari per il fov della camera). Per evitare spreco di memoria e carico di lavoro di opengl (avendo da collegare pochi frammenti a tanti texel) si usano le mipmap.

L'idea è quella di creare una collezione della stessa texture che mano mano riduce la sua risoluzione

![[Pasted image 20250905172141.png]]

e in seguito ad un certo threshold dal punto di vista dell'utente, OpenGL usa una differente texture mipmap in modo da usare una più piccola, in quanto se un'oggetto è distante dall'utente, la risoluzione minore della texture appena applicata non sarà così visibile all'utente
```cpp
glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_LINEAR_MIPMAP_LINEAR);
glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR);
```


---
### caricare e creare texture

c'è una libreria popolare usata per caricare texture ed è stb_image.h

per caricare una texture si usa

```cpp
int width, height, nrChannels;
unsigned char *data = stbi_load("container.jpg", &width, &height, &nrChannels, 0); 
```

stb_load si occuperà di assegnare i valori ai tre interi. Una volta caricata la texture la dobbiamo generare in opengl

```cpp
unsigned int texture;
glGenTextures(1, &texture); // (number of textures, array of stored texture)
```

dobbiamo legare la texture al target OpenGL GL_TEXTURE_2D

```cpp
glBindTexture(GL_TEXTURE_2D, texture);  
```

ora si può generare la texture usando l'immagine caricata di prima 

```cpp
glTexImage2D(GL_TEXTURE_2D, 0, GL_RGB, width, height, 0, GL_RGB, GL_UNSIGNED_BYTE, data);
glGenerateMipmap(GL_TEXTURE_2D);
```

- **Primo argomento**: specifica il _target della texture_. Impostandolo a `GL_TEXTURE_2D`, l’operazione genererà una texture sull’oggetto texture attualmente collegato a quel target (le texture collegate a `GL_TEXTURE_1D` o `GL_TEXTURE_3D` non saranno interessate).
    
- **Secondo argomento**: specifica il _livello di mipmap_ per cui creare la texture. Se si vuole, è possibile impostare manualmente ogni livello; in questo caso, lo lasciamo al livello base `0`.
    
- **Terzo argomento**: indica a OpenGL in quale _formato_ memorizzare la texture. L’immagine ha valori solo RGB, quindi useremo anche per la texture il formato RGB.
    
- **Quarto e quinto argomento**: definiscono la _larghezza_ e l’_altezza_ della texture risultante. Questi valori sono stati salvati in precedenza durante il caricamento dell’immagine e useremo le variabili corrispondenti.
    
- **Sesto argomento**: deve essere sempre `0` (questioni di compatibilità con versioni legacy).
    
- **Settimo e ottavo argomento**: specificano il _formato_ e il _tipo di dato_ dell’immagine sorgente. Poiché l’immagine è stata caricata con valori RGB e memorizzata come caratteri (byte), passeremo i valori corrispondenti.
    
- **Ultimo argomento**: rappresenta i _dati effettivi dell’immagine_.

Con questo ora l'oggetto texture ora è legato con l'immagine texture. In seguito si può liberare la memoria in cpu

```cpp
stbi_image_free(data);
```


---
### texture e shader

le coordinate texture sono aggiunte come un attributo dei vertici oltre alla posizione, colori

```cpp
float vertices[] = {
    // positions          // colors           // texture coords
     0.5f,  0.5f, 0.0f,   1.0f, 0.0f, 0.0f,   1.0f, 1.0f,   // top right
     0.5f, -0.5f, 0.0f,   0.0f, 1.0f, 0.0f,   1.0f, 0.0f,   // bottom right
    -0.5f, -0.5f, 0.0f,   0.0f, 0.0f, 1.0f,   0.0f, 0.0f,   // bottom left
    -0.5f,  0.5f, 0.0f,   1.0f, 1.0f, 0.0f,   0.0f, 1.0f    // top left 
};
```

si aggiorna il VAO

![[Pasted image 20250905191157.png]]
(bisogna aggiornare lo stride degli altri attributi in caso)

ora bisogna aggiornare il vertex shader aggiungendo un nuovo layout per accettare le coordinate texture e fare una variabile out per passarle al fragment

```cpp
layout (location = 0) in vec3 aPos;
layout (location = 1) in vec3 aColor;
layout (location = 2) in vec2 aTexCoord;

out vec3 ourColor;
out vec2 TexCoord;

void main()
{
    gl_Position = vec4(aPos, 1.0);
    ourColor = aColor;
    TexCoord = aTexCoord;
}
```

oltre alle coordinate texture, il fragment shader ha bisogno dell'accesso all'oggetto texture, la si passa con una uniform con sampler2D

```cpp
out vec4 FragColor;
  
in vec3 ourColor;
in vec2 TexCoord;

uniform sampler2D ourTexture;

void main()
{
    FragColor = texture(ourTexture, TexCoord);
}
```

per campionare il colore della texture c'è una funzione apposta che si chiama texture che ha come primo argomento l'oggetto texture e come secondo argomento la coordinate texture da dove campionare

l'output sarà il colore filtrato della texture alla coordinate texture interpolata