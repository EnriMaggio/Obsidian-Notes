il vertex array object non salva direttamente dati di vertici, invece contiene informazioni su come recuperare dati sui vertici per il loro attributo.

Gli attributi dei vertici possono essere
- posizione
- colore
- normali

![[Pasted image 20250904180606.png]]
![[Pasted image 20250904180649.png]]

per assegnare che tipo di attributi assegnare ai vertici del buffer si utilizza glVertexAttribPointer
- primo arg: locazione descritto nello shader
- secondo arg: dimensione di un singolo vertice
- terzo arg: tipo(int,float ecc. ecc.) del vertice
- quarto arg: se si vuole normalizzazione
- quinto arg: stride o salto che OpenGL deve effettuare per leggere il prossimo vertice di quel specifico attributo
- sesto arg: dove iniziare a leggere in memoria
. Di seguito bisogna anche abilitarli

```cpp
glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 3 * sizeof(float), (void*)0);
glEnableVertexAttribArray(0);
```

una volta fatto il legamento in gpu il buffer non ci serve più, perchè è stato caricato tutto in gpu

