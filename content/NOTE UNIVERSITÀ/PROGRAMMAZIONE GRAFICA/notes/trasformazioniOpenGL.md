Le trasformazioni permettono agli oggetti della scena di avere dinamicità, si può cambiare i vertici a runtime cambiando i buffer a ogni frame, ma ovviamente quando i vertici diventano tanti diventa impossibili gestirli manualmente singolarmente

Per questo esistono le [[trasformazioni]] che sono matrici di oggetto da applicare agli oggetti 3d


---
### GLM

OpenGL non ha costrutti o funzioni che creano o gestiscono queste matrici, per fortuna c'è la libreria [GLM](https://glm.g-truc.net/0.9.8/index.html) e comprende solo degli header file

```cpp
#include <glm/glm.hpp>
#include <glm/gtc/matrix_transform.hpp>
#include <glm/gtc/type_ptr.hpp>
```

un esempio di trasformazione può essere lo scalare

```cpp
glm::vec4 vec(1.0f, 0.0f, 0.0f, 1.0f);
glm::mat4 trans = glm::mat4(1.0f);
trans = glm::translate(trans, glm::vec3(1.0f, 1.0f, 0.0f));
vec = trans * vec;
std::cout << vec.x << vec.y << vec.z << std::endl;
```

il vettore in questo esempio è stato traslato di 1 nei componenti x e y

La cosa più importante però è come passare queste trasformazioni agli shader, semplicmente basta con degli uniform. Si possono fare le trasformazioni anche negli shader

```cpp
#version 330 core
layout (location = 0) in vec3 aPos;
layout (location = 1) in vec2 aTexCoord;

out vec2 TexCoord;
  
uniform mat4 transform;

void main()
{
    gl_Position = transform * vec4(aPos, 1.0f);
    TexCoord = vec2(aTexCoord.x, aTexCoord.y);
} 
```

```cpp
unsigned int transformLoc = glGetUniformLocation(ourShader.ID, "transform");
glUniformMatrix4fv(transformLoc, 1, GL_FALSE, glm::value_ptr(trans));
```
