Gli oggetti nella reltà non hanno un solo materiale, spesso ne hanno di più.

Per questo ci vengono in aiuto le mappe diffus e speculari fornendoci una migliore precisazione di come l'oggetto reagisce in presenza di luci.


---
### diffuse map

l'idea è quella di fornire per ogni frammento il suo colore di diffuse. Lo si fa con una texture che si chiama diffuse map, un immagine che contiene i colori diffuse per ogni frammento

![[Pasted image 20250908155125.png]]

essendo una texture usiamo un Sampler2D come tipo e la inseriamo nella struct

```cpp
struct Material { 
	sampler2D diffuse; 
	vec3 specular; 
	float shininess; 
}; 
... 
in vec2 TexCoords;
```
(il componente ambientale non è presente, perchè simile al diffuse colore, e ormai la luce ambientale è gestita dalla struct luce)

Siccome è una texture, ci servono le coordinate texture (sia nel codice aggiornando vao ecc.)

vertex shader
```cpp
#version 330 core
layout (location = 0) in vec3 aPos;
layout (location = 1) in vec3 aNormal;
layout (location = 2) in vec2 aTexCoords;

out vec3 FragPos;
out vec3 Normal;
out vec2 TexCoords;

uniform mat4 model;
uniform mat4 view;
uniform mat4 projection;

void main()
{
    FragPos = vec3(model * vec4(aPos, 1.0));
    Normal = mat3(transpose(inverse(model))) * aNormal;  
    TexCoords = aTexCoords;
    
    gl_Position = projection * view * vec4(FragPos, 1.0);
}
```

fragment shader
```cpp
out vec4 FragColor;

struct Material {
    sampler2D diffuse;
    vec3 specular;    
    float shininess;
}; 

struct Light {
    vec3 position;

    vec3 ambient;
    vec3 diffuse;
    vec3 specular;
};

in vec3 FragPos;  
in vec3 Normal;  
in vec2 TexCoords;
  
uniform vec3 viewPos;
uniform Material material;
uniform Light light;

void main()
{
    // ambient
    vec3 ambient = light.ambient * texture(material.diffuse, TexCoords).rgb;
  	
    // diffuse 
    vec3 norm = normalize(Normal);
    vec3 lightDir = normalize(light.position - FragPos);
    float diff = max(dot(norm, lightDir), 0.0);
    vec3 diffuse = light.diffuse * diff * texture(material.diffuse, TexCoords).rgb;  
    
    // specular
    vec3 viewDir = normalize(viewPos - FragPos);
    vec3 reflectDir = reflect(-lightDir, norm);  
    float spec = pow(max(dot(viewDir, reflectDir), 0.0), material.shininess);
    vec3 specular = light.specular * (spec * material.specular);  
        
    vec3 result = ambient + diffuse + specular;
    FragColor = vec4(result, 1.0);
} 
```

ora in diffuse si usa la funzione texture per campionare il colore alla giusta posizione nella texture

![[Pasted image 20250908155818.png]]

---
### Specular map

Le specular map aiutano a determinare quali sezioni dei materiali riflettono o no. Lo si fa con un'altra texture, essa specifica le intensità dei riflessi di ogni frammento del materiale

![[Pasted image 20250908160135.png]]
(per semplicità bianco e nero)

L'intensità della luce speculare deriva dalla luminosità di ciascun pixel nell'immagine. Ogni pixel della mappa speculare può essere visualizzato come un vettore di colore, dove il nero rappresenta il vettore di colore vec3(0.0) e il grigio il vettore di colore vec3(0.5), ad esempio.

Nel fragment shader, campioniamo quindi il valore di colore corrispondente e moltiplichiamo questo valore per l'intensità speculare della luce. Più un pixel è "bianco", maggiore è il risultato della moltiplicazione e quindi più luminosa diventa la componente speculare di un oggetto.

Essendo una seconda texture dobbiamo generarla

```cpp
lightingShader.setInt("material.specular", 1);
...
glActiveTexture(GL_TEXTURE1);
glBindTexture(GL_TEXTURE_2D, specularMap);  
```

ora la struct dei materiali si aggiorna

```cpp
struct Material {
    sampler2D diffuse;
    sampler2D specular;
    float     shininess;
};  
```

il fragment shader
```cpp
#version 330 core
out vec4 FragColor;

struct Material {
    sampler2D diffuse;
    sampler2D specular;    
    float shininess;
}; 

struct Light {
    vec3 position;

    vec3 ambient;
    vec3 diffuse;
    vec3 specular;
};

in vec3 FragPos;  
in vec3 Normal;  
in vec2 TexCoords;
  
uniform vec3 viewPos;
uniform Material material;
uniform Light light;

void main()
{
    // ambient
    vec3 ambient = light.ambient * texture(material.diffuse, TexCoords).rgb;
  	
    // diffuse 
    vec3 norm = normalize(Normal);
    vec3 lightDir = normalize(light.position - FragPos);
    float diff = max(dot(norm, lightDir), 0.0);
    vec3 diffuse = light.diffuse * diff * texture(material.diffuse, TexCoords).rgb;  
    
    // specular
    vec3 viewDir = normalize(viewPos - FragPos);
    vec3 reflectDir = reflect(-lightDir, norm);  
    float spec = pow(max(dot(viewDir, reflectDir), 0.0), material.shininess);
    vec3 specular = light.specular * spec * texture(material.specular, TexCoords).rgb;  
        
    vec3 result = ambient + diffuse + specular;
    FragColor = vec4(result, 1.0);
} 
```

![[Pasted image 20250908160729.png]]