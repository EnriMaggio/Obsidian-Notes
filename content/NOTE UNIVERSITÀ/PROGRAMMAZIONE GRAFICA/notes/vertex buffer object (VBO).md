
alcuni stati in opengl sono incapsulati usando oggetti, ogni oggetto ha un tipo e uno di questi tipi è il buffer

gli oggetti in opengl hanno dei nomi che però sono interi (non stringhe di caratteri)

Si usa il vbo o vao (dopo) per salvare questi nomi

si può gestire la memoria della gpu tramite i cosiddetti **vertex buffer objects** (VBO), che possono memorizzare un gran numero di vertici nella memoria della GPU. Il vantaggio di usare questi buffer è che possiamo inviare grandi lotti di dati tutti in una volta alla scheda grafica e, se c'è abbastanza memoria, mantenerli lì senza dover inviare i dati un vertice alla volta.

Inviare dati alla scheda grafica dalla CPU è un processo relativamente lento, per cui, ogni volta che è possibile, cerchiamo di inviare quanti più dati possibile in una sola volta. Una volta che i dati si trovano nella memoria della scheda grafica, lo **shader dei vertici** ha un accesso quasi istantaneo ai vertici, rendendo l'operazione estremamente veloce.

il vbo è un oggetto OpenGL ed è un intero senza segno che salva nomi per oggetti di opengl
![[Pasted image 20250904173142.png]]
per il vbo si utilizza il comando
```cpp
unsigned int VBO;
glGenBuffers(1, &VBO);
```

In opengl si possono legare oggetti con i target

Opengl ha tanti tipi di oggetti buffer e il TIPO BUFFER di un vertex buffer object è GL_ARRAY_BUFFER e si può legare con il nuovo buffer con il comando 

```cpp
glBindBuffer(GL_ARRAY_BUFFER, VBO);
```
![[Pasted image 20250904173603.png]]

Per il momento non ci sono dati nel buffer, per copiare dei dati si utilizza il seguente comando

```cpp
glBufferData(GL_ARRAY_BUFFER, sizeof(vertices), vertices, GL_STATIC_DRAW);
```
  
