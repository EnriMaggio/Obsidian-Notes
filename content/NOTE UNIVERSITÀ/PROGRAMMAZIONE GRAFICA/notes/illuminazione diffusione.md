la diffusione della luce comincia a illuminare come nella realtà un oggetto. Quello che fa è rendere l'oggetto più illuminato se i frammenti della scena sono allineati ai raggi della sorgente di luce

![[Pasted image 20250908112704.png]]

In Pratica Per tutti i frammenti, dobbiamo calcolare l'angolo che si forma tra il raggio della luce e il singolo frammento. In base all'angolo la superficie risulterà più illuminata o scura.

Per misurare l'angolo serve il vettore normale perpendicolare alla superficie dell'oggetto, in seguito basta fare il prodotto scalare (dot product) dei due vettori

**![[Pasted image 20250908113413.png]]

Il risultato del prodotto scalare è un valore che possiamo utilizzare per calcolare l'impatto della luce nel colore del frammento


---
### codice illuminazione diffusa

Siccome si lavora in vertici, il vettore normale non è gratis, bisogna calcolarlo aiutandosi con gli altri vertici per capire prima la superficie, per poi trovare la normale (utilizzando il prodotto vettoriale)

Nel caso di un cubo possiamo passare le normali delle superficii essendo un oggetto semplice. Le normali possono essere aggiunte come attributi dei vertici

```cpp
float vertices[] = {
	// prima faccia
    -0.5f, -0.5f, -0.5f,  0.0f,  0.0f, -1.0f,
     0.5f, -0.5f, -0.5f,  0.0f,  0.0f, -1.0f, 
     0.5f,  0.5f, -0.5f,  0.0f,  0.0f, -1.0f, 
     0.5f,  0.5f, -0.5f,  0.0f,  0.0f, -1.0f, 
    -0.5f,  0.5f, -0.5f,  0.0f,  0.0f, -1.0f, 
    -0.5f, -0.5f, -0.5f,  0.0f,  0.0f, -1.0f,
    // seconda faccia 
	-0.5f, -0.5f,  0.5f,  0.0f,  0.0f, 1.0f,
     0.5f, -0.5f,  0.5f,  0.0f,  0.0f, 1.0f,
     0.5f,  0.5f,  0.5f,  0.0f,  0.0f, 1.0f,
     0.5f,  0.5f,  0.5f,  0.0f,  0.0f, 1.0f,
    -0.5f,  0.5f,  0.5f,  0.0f,  0.0f, 1.0f,
    -0.5f, -0.5f,  0.5f,  0.0f,  0.0f, 1.0f,
	// ...il resto dei vertici...
};
```

ovviamente si aggiorano il vertex shader, i buffer objects e i vao

```cpp
#version 330 core
layout (location = 0) in vec3 aPos;
layout (location = 1) in vec3 aNormal;

out vec3 Normal; // dobbiamo protare le normali al fragment shader

void main()
{
    gl_Position = projection * view * model * vec4(aPos, 1.0);
    Normal = aNormal;
} 
```

```cpp
glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 6 * sizeof(float), (void*)0);
glEnableVertexAttribArray(0);
// abilitiamo le normai
glVertexAttribPointer(1, 3, GL_FLOAT, GL_FALSE, 6 * sizeof(float), (void*)(3 * sizeof(float)));
    glEnableVertexAttribArray(1);
```

Siccome dobbiamo calcolare l'illuminazione diffusa per frammento, abbiamo bisogno di portare il vertice nello spazio mondo e passarlo come out al fragment shader

```cpp
out vec3 FragPos;  
out vec3 Normal;
  
void main()
{
    gl_Position = projection * view * model * vec4(aPos, 1.0);
    FragPos = vec3(model * vec4(aPos, 1.0));
    Normal = aNormal;
}
```


Abbiamo bisogno anche del vettore che ci dice la posizione della sorgente di luce, siccome è statico e singolo possiamo metterlo come uniform e passarlo direttamente al fragment shader più gli altri attibuti

```cpp
#version 330 core
out vec4 FragColor;

in vec3 Normal;  
in vec3 FragPos;  // interpolato dai 3 vettori dello spazio mondo del triangolo
  
uniform vec3 lightPos; 
uniform vec3 lightColor;
uniform vec3 objectColor;

void main()
{
    // ambient
    float ambientStrength = 0.1;
    vec3 ambient = ambientStrength * lightColor;
  	
    // diffuse 
    vec3 norm = normalize(Normal);
    vec3 lightDir = normalize(lightPos - FragPos);
    float diff = max(dot(norm, lightDir), 0.0);
    vec3 diffuse = diff * lightColor;
            
    vec3 result = (ambient + diffuse) * objectColor;
    FragColor = vec4(result, 1.0);
} 
```

come descritto nel codice dobbiamo
- calcolare il vettore che indica la direzione della luce de tra sorgente di luce e frammento
- normalizzare (ci interessa l'orientazione e non il magnitudo)
- prodotto scalare tra normale e vettore della direzione della luce e fare il massimo tra 0.0 e 1.0 (non ci sono colori negativi)
- prodotto con lo scalare appena trovato con il colore della sorgente di luce
- sommare all'ambient e moltiplicazione vettoriale con il colore dell'oggetto

![[Pasted image 20250908142015.png]]