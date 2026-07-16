Sapendo come funzionano le trasformazioni, ora possiamo finalmente renderizzare oggetti 3d nella nostra scena

Per renderizzare un cubo ci voglion 36 vertici (6 facce * 2 triangoli * 3 vertici)
```cpp
float vertices[] = {
    -0.5f, -0.5f, -0.5f,  0.0f, 0.0f,
     0.5f, -0.5f, -0.5f,  1.0f, 0.0f,
     0.5f,  0.5f, -0.5f,  1.0f, 1.0f,
     0.5f,  0.5f, -0.5f,  1.0f, 1.0f,
    -0.5f,  0.5f, -0.5f,  0.0f, 1.0f,
    -0.5f, -0.5f, -0.5f,  0.0f, 0.0f,

    -0.5f, -0.5f,  0.5f,  0.0f, 0.0f,
     0.5f, -0.5f,  0.5f,  1.0f, 0.0f,
     0.5f,  0.5f,  0.5f,  1.0f, 1.0f,
     0.5f,  0.5f,  0.5f,  1.0f, 1.0f,
    -0.5f,  0.5f,  0.5f,  0.0f, 1.0f,
    -0.5f, -0.5f,  0.5f,  0.0f, 0.0f,

    -0.5f,  0.5f,  0.5f,  1.0f, 0.0f,
    -0.5f,  0.5f, -0.5f,  1.0f, 1.0f,
    -0.5f, -0.5f, -0.5f,  0.0f, 1.0f,
    -0.5f, -0.5f, -0.5f,  0.0f, 1.0f,
    -0.5f, -0.5f,  0.5f,  0.0f, 0.0f,
    -0.5f,  0.5f,  0.5f,  1.0f, 0.0f,

     0.5f,  0.5f,  0.5f,  1.0f, 0.0f,
     0.5f,  0.5f, -0.5f,  1.0f, 1.0f,
     0.5f, -0.5f, -0.5f,  0.0f, 1.0f,
     0.5f, -0.5f, -0.5f,  0.0f, 1.0f,
     0.5f, -0.5f,  0.5f,  0.0f, 0.0f,
     0.5f,  0.5f,  0.5f,  1.0f, 0.0f,

    -0.5f, -0.5f, -0.5f,  0.0f, 1.0f,
     0.5f, -0.5f, -0.5f,  1.0f, 1.0f,
     0.5f, -0.5f,  0.5f,  1.0f, 0.0f,
     0.5f, -0.5f,  0.5f,  1.0f, 0.0f,
    -0.5f, -0.5f,  0.5f,  0.0f, 0.0f,
    -0.5f, -0.5f, -0.5f,  0.0f, 1.0f,

    -0.5f,  0.5f, -0.5f,  0.0f, 1.0f,
     0.5f,  0.5f, -0.5f,  1.0f, 1.0f,
     0.5f,  0.5f,  0.5f,  1.0f, 0.0f,
     0.5f,  0.5f,  0.5f,  1.0f, 0.0f,
    -0.5f,  0.5f,  0.5f,  0.0f, 0.0f,
    -0.5f,  0.5f, -0.5f,  0.0f, 1.0f
};
```


quindi dobbiamo definire per primo una matrice model che conterrà le trasformazioni desiderate

```cpp
glm::mat4 model = glm::mat4(1.0f);
model = glm::rotate(model, (float)glfwGetTime() * glm::radians(50.0f), glm::vec3(0.5f, 1.0f, 0.0f)); 
```
(il cubo fa una rortazione per l'angolo specificato nel secondo argomento e ruotra intorno  agli assi x e y)

da teoria sappiamo che se moltiplichiamo i vertici con la matrice model otteniamo le coordinate di quei vertici nello spazio mondo.

Successivamente dobbiamo creare una matrice di vista (view matrix).
Vogliamo spostarci leggermente indietro nella scena in modo che l’oggetto diventi visibile (quando ci troviamo nello spazio del mondo siamo posizionati all’origine (0,0,0)).

Per muoversi all’interno della scena, bisogna pensare a questo:
- Spostare la camera all’indietro equivale a spostare tutta la scena in avanti.
 - Ed è esattamente ciò che fa la view matrix: muove l’intera scena in modo inverso rispetto alla direzione in cui vogliamo spostare la camera.

Poiché vogliamo muoverci all’indietro e, dato che OpenGL utilizza un sistema destro (right-handed system), dobbiamo muoverci lungo l’asse z positivo. Facciamo questo traslando la scena verso l’asse z negativo. Questo dà l’impressione che ci stiamo muovendo all’indietro.

Per convenzione l'asse z negativo punta alla scena, mentre il positivo alla vista dell'utente

Per convenzione, OpenGL utilizza un sistema destro. In pratica significa che:

- l’asse **x positivo** è verso destra,
- l’asse **y positivo** è verso l’alto,
- l’asse **z positivo** è “verso l’esterno” dallo schermo, quindi verso di noi, mentre lo **z negativo** entra nello schermo.

Immagina lo schermo come il centro dei 3 assi, con l’asse z positivo che attraversa lo schermo verso l’osservatore.

>Nota: nelle **coordinate normalizzate del dispositivo** (_NDC_), OpenGL in realtà utilizza un sistema sinistro, perché la **matrice di proiezione** inverte la mano del sistema di riferimento.

La matrice view quindi ad esempio è

```cpp
glm::mat4 view = glm::mat4(1.0f);
// note that we're translating the scene in the reverse direction of where we want to move
view = glm::translate(view, glm::vec3(0.0f, 0.0f, -3.0f)); 
```

e per ultimo si utilizza la projection matrix per la scena che utilizzerà una proiezione prospettica,

```cpp
glm::mat4 projection;
projection = glm::perspective(glm::radians(45.0f), 800.0f / 600.0f, 0.1f, 100.0f);
```

ora che ce le abbiamo, le matrici le mettiamo come uniform le passiamo al vertex shader

```cpp
int modelLoc = glGetUniformLocation(ourShader.ID, "model");
glUniformMatrix4fv(modelLoc, 1, GL_FALSE, glm::value_ptr(model));
... // si fa lo stesso per la matrice view e projection
```

```cpp
#version 330 core
layout (location = 0) in vec3 aPos;
...
uniform mat4 model;
uniform mat4 view;
uniform mat4 projection;

void main()
{
    // la moltiplicazione si legge da destra a sinistra
    gl_Position = projection * view * model * vec4(aPos, 1.0);
    ...
}
```

nel render loop bisogna chiamare

```cpp
glDrawArrays(GL_TRIANGLES, 0, 36);
```

il risultato è
![[Pasted image 20250906113634.png]]

si nota che c'è un problema di sovrapposizione, dove alcune facce(che stanno dietro e dunque non dovrebbero essere renderizzate) potrebbero essere renderizzate sopra ad altre facce.

Questo perchè OpenGL quando disegna il cubo triangolo per triangolo, frammento per frammento, lui sovradisegna ogni colore dei pixel che magari sono già stati disegnati prima. Queto perchè non c'è un ordine con qui OpenGL renderizza i triangoli.

Per fortuna OpenGL salva informazioni sulla profondità dei veritici nel z-buffer conosciuto come buffer di profondità, in pratica il buffer contiene la profondità o coordinata z dei  frammenti, e qualora il frammento vuole dare in output il suo colore, OpenGL compara il suo valore di profondità con quello del z buffer. Se il frammento corrente è dietro all'altro, allora il primo viene scartato. Il processo è chiamato depth testing.

Bisogna abilitare il depth testing e lo z buffer

```cpp
glEnable(GL_DEPTH_TEST); 
```

prima di ogni iterazione del render bisogna pulire il depth buffer (se no le informazioni sul depth del frame precedente rimangono sul buffer della memoria)

```cpp
glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
```

![[Pasted image 20250906121214.png]]