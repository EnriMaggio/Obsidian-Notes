Nel mondo reale, ogni oggetto reagisce in maniera differente quando sono esposti alla luce.

Quando descriviamo un materiale per un oggetto in OpenGL è più sensato realizzare una struct material avendo come dati le proprietà intrinsiche del materiale della superficie in termni di luminosità

```cpp
#version 330 core
struct Material {
    vec3 ambient; // colore che riflette nella luce ambientale
    vec3 diffuse; // colore della superficie sotto diffuse lighting
    vec3 specular; // colore della luce riflessa sulla superficie
    float shininess; // indica quanto è lucente il materiale 
}; 
  
uniform Material material;
```

con questi 4 parametri è possibile simulare materiali reali

![[Pasted image 20250908153210.png]]

Il fragment sarà

```cpp
#version 330 core
struct Material {
    vec3 ambient; // colore che riflette nella luce ambientale
    vec3 diffuse; // colore della superficie sotto diffuse lighting
    vec3 specular; // colore della luce riflessa sulla superficie
    float shininess; // indica quanto è lucente il materiale 
}; 
  
uniform Material material;

void main()
{    
    // ambient
    vec3 ambient = lightColor * material.ambient;
  	
    // diffuse 
    vec3 norm = normalize(Normal);
    vec3 lightDir = normalize(lightPos - FragPos);
    float diff = max(dot(norm, lightDir), 0.0);
    vec3 diffuse = lightColor * (diff * material.diffuse);
    
    // specular
    vec3 viewDir = normalize(viewPos - FragPos);
    vec3 reflectDir = reflect(-lightDir, norm);  
    float spec = pow(max(dot(viewDir, reflectDir), 0.0), material.shininess);
    vec3 specular = lightColor * (spec * material.specular);  
        
    vec3 result = ambient + diffuse + specular;
    FragColor = vec4(result, 1.0);
}
```

La struct funge da namespace per delle variabili in GLSL. Per popolare la struct, basta riferirisi al nome di essa con  . per accedere ai suoi elementi

```cpp
lightingShader.setVec3("material.ambient", 1.0f, 0.5f, 0.31f);
lightingShader.setVec3("material.diffuse", 1.0f, 0.5f, 0.31f);
lightingShader.setVec3("material.specular", 0.5f, 0.5f, 0.5f);
lightingShader.setFloat("material.shininess", 32.0f);
```

![[Pasted image 20250908153718.png]]

risulta tutto chiaro perchè le componenti del materiale sono riflesse con la massima forza da qualsiasi tipo di sorgente di luce.

Anche le sorgenti di luce hanno diverse intensità per quanto riguarda le sue componenti ambientali, diffusione e specularità. Si può risolvere moltiplicando con un vettore a 3 dimensioni che indica l'intensità di ognuno dei componenti

```cpp
vec3 ambient  = vec3(1.0) * material.ambient;
vec3 diffuse  = vec3(1.0) * (diff * material.diffuse);
vec3 specular = vec3(1.0) * (spec * material.specular); 
```

A questo punto, come con i materiali, si può fare una struct anche per la luce

```cpp
struct Light {
    vec3 position; // posizione della luce
    vec3 ambient; // di solito basso
    vec3 diffuse;
    vec3 specular;
};

uniform Light light;  
```

adesso il fragment shader cambierà l'utilizzo delle variabili

```cpp
vec3 ambient  = light.ambient * material.ambient;
vec3 diffuse  = light.diffuse * (diff * material.diffuse);
vec3 specular = light.specular * (spec * material.specular);  
```

e nel render loop settiamo le componenti della luce 

```cpp
lightingShader.setVec3("light.ambient",  0.2f, 0.2f, 0.2f);
lightingShader.setVec3("light.diffuse",  0.5f, 0.5f, 0.5f); // darken diffuse light a bit
lightingShader.setVec3("light.specular", 1.0f, 1.0f, 1.0f); 
```

![[Pasted image 20250908154535.png]]