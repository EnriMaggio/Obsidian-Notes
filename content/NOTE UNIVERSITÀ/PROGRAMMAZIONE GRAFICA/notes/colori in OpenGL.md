Per rappresentare digitalmente i colori nei computer si usano le tre componenti 
RGB (rosso, verde, blu)

quindi possiamo dichiarare un vettore con tre componenti con valori cha vanno da 0.0 a 1.0, in modo anche da ottenere una combinazione di quei colori se si ha necessità

```cpp
glm::vec3 coral(1.0f, 0.5f, 0.31f);   
```

Per farla breve il colore di un oggetto nella vita reale non è il colore che attualmente ha, ma è il colore che riflette l'oggetto, i colori che non sono assorbiti dall'oggetto vengono visti dalla percezione dei nostri occhi. La luce del sole è bianca perchè contiene tutti i colori, quindi quando punta un oggetto di un colore, l'oggetto assorbe i colori che non sono suoi, il resto lo riflette

![[Pasted image 20250908101821.png]]
(l'oggetto ha assorbito il viola,blu ecc. ecc.)

In OpenGL la riflessione del colore funziona più o meno nello stesso modo. Per iniziare bisogna creare una fonte di luce e quindi dobbiamo dare i suoi colori

```cpp
glm::vec3 lightColor(1.0f, 1.0f, 1.0f);
glm::vec3 toyColor(1.0f, 0.5f, 0.31f);
glm::vec3 result = lightColor * toyColor; // = (1.0f, 0.5f, 0.31f);
```

se si moltiplica componente per componente il colore della luce e il colore dell'oggetto otteniamo il colore riflesso. L'oggetto di un colore è infine l'ammontare di ogni colore di riflettere da una sorgente di luce.

Essendo che si tratta di colori, il lavoro per stabilire il colore finale sarà fatto sul fragment shader. Per semplicità si crea un cubo che funge da sorgente di luce (aggiornando il vao, buffer ecc. ecc.)

```cpp
unsigned int lightVAO;
glGenVertexArrays(1, &lightVAO);
glBindVertexArray(lightVAO);
// we only need to bind to the VBO, the container's VBO's data already contains the data.
glBindBuffer(GL_ARRAY_BUFFER, VBO);
// set the vertex attribute 
glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 3 * sizeof(float), (void*)0);
glEnableVertexAttribArray(0);
```

essendo un altro oggetto due coppie di shader, uno per l'oggetto che deve riflettere la luce e un altro per la sorgente di luce. Il vertex è simile per entrambi

```cpp
#version 330 core
layout (location = 0) in vec3 aPos;

uniform mat4 model;
uniform mat4 view;
uniform mat4 projection;

void main()
{
    gl_Position = projection * view * model * vec4(aPos, 1.0);
} 
```

mentre il fragmente dell'oggetto che deve riflettere è

```cpp
#version 330 core
out vec4 FragColor;
  
uniform vec3 objectColor;
uniform vec3 lightColor;

void main()
{
    FragColor = vec4(lightColor * objectColor, 1.0);
}
```

mentre della sorgente di luce

```cpp
#version 330 core
out vec4 FragColor;

void main()
{
    FragColor = vec4(1.0); // set all 4 vector values to 1.0
}
```

Per il momento si usa una sorgente di luce visibile per vedere da dove arriva la luce. Per far vedere la sorgente di luce dobbiamo piazzare un cubo nella stessa posizione della sorgente di luce. Poi con il secondo shader, il cubo sarà colorato di bianco 

```cpp
glm::vec3 lightPos(1.2f, 1.0f, 2.0f); // spazio mondo
```

Poi trasliamo il cubo nella stessa posizione della sorgente di luce

```cpp
model = glm::mat4(1.0f);
model = glm::translate(model, lightPos);
model = glm::scale(model, glm::vec3(0.2f)); 
```

Per poi renderizzare nel render loop

```cpp
lightCubeShader.use();
// set the model, view and projection matrix uniforms
[...]
// draw the light cube object
glBindVertexArray(lightCubeVAO);
glDrawArrays(GL_TRIANGLES, 0, 36);
```

![[Pasted image 20250908105245.png]]