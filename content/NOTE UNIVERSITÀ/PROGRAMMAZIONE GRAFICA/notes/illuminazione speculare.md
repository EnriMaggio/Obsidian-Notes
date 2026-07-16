abbiamo già visto che nell'illuminazione [[Specular]], è presente l'osservatore che capta i riflessi della luce, questa illuminazione dipende fortemente dalla direzione della vista.

L'illuminazione si basa anche sulle proprietà riflettenti delle superfici degli oggetti.

![[Pasted image 20250908142327.png]]

bisogna trovare quindi l'angolo tra il vettore riflesso e il vettore che indice la direzione del punto di vista.

Più l'angolo è acuto (più vicini sono) e maggiore sarà l'impatto del riflesso speculare, si vedrà una sorta di chiazza bianca.

Per trovare il vettore direzione della vista abbiamo bisogno del vettore che indica la sua posizione e il vettore che indica la posizione del frammento che riflette la luce.

Per questo passiamo nel fragment shader, con una uniform, la posizione del punto di vista (in questo caso la posizione della camera)

```cpp
#version 330 core
out vec4 FragColor;

in vec3 Normal;  
in vec3 FragPos;  
  
uniform vec3 lightPos; 
uniform vec3 viewPos; 
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
    
    // specular
    float specularStrength = 0.5;
    vec3 viewDir = normalize(viewPos - FragPos);
    vec3 reflectDir = reflect(-lightDir, norm);  
    float spec = pow(max(dot(viewDir, reflectDir), 0.0), 32);
    vec3 specular = specularStrength * spec * lightColor;  
        
    vec3 result = (ambient + diffuse + specular) * objectColor;
    FragColor = vec4(result, 1.0);
} 
```

per calcolare la specularità bisogna
- stabilire l'intensità speculare
- calcolare il vettore direzione (sottrazione tra viewPos e FragPos)
- riflettere il raggio di luce negando la direzione della luce, questo perchè la funzione reflect si aspetta come primo argomento il vettore che dalla sorgente di luce punta al frammento. Attualmente il vettore della direzione della luce è al contrario (dal frammento alla sorgente di luce)
- calcolare la componente speculare finale con il prodotto scalare tra direzione vista e direzione del riflesso e poi elevarlo alal potenza di 32. Per 32 indichiamo il valore di lucentezza 
	![[Pasted image 20250908143917.png]]
- moltiplicare l'intensità speculare, il riflesso percepito, il colore dell'oggetto

e nel render loop settiamo la uniform della posizione del punto di vista

```cpp
lightingShader.use();
        lightingShader.setVec3("objectColor", 1.0f, 0.5f, 0.31f);
        lightingShader.setVec3("lightColor", 1.0f, 1.0f, 1.0f);
        lightingShader.setVec3("lightPos", lightPos);
        lightingShader.setVec3("viewPos", camera.Position);
```

![[Pasted image 20250908144147.png]]