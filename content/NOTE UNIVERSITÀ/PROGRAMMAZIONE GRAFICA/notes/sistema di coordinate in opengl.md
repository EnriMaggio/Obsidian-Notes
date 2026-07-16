il sistema di coordinate in opengl si aspetta che i vertici degli oggetti siano normalizzati dopo ogni compilazione del vertex shader

Per normalizzazione si intende che i valori delle coordinate x,y,x devono essere compresi tra -1.0 e 1.0, le coordinate che sono al di fuori di questo range non saranno visibili

Quello che si limita il programmatore è quello di specificare coordinate dentro un range che nel vertex shader verranno trasformate in coordinate NDC (normalized device coordinates), di seguito saranno date in input al rasterizer per trasformarle in coordinate 2d

Il processo per trasformare le coordinate in NDC inizia da:
- trasformare i vertici dell'oggetto in un insieme di sistemi di riferimento
- trasformazione delle coordinate in NDC

Ci sono delle trasformazioni intermedie perchè alcune operazioni sono più facili da computare con certi sistemi di riferimento.

abbiamo già visto le trasformazioni ed infine il calcolo finale risulta

![[Pasted image 20250906105254.png]]

da notare che l'ordine delle matrici è inverso perchè la moltiplicazione va da destra a sinsitra. Il risultato che è un vertice verrà assegnato a gl_position nel vertex shader

L’output del vertex shader richiede che le coordinate siano nello spazio di clip (clip-space), cosa che abbiamo ottenuto grazie alle matrici di trasformazione.

OpenGL esegue poi la divisione prospettica (perspective division) sulle coordinate in clip-space per trasformarle in coordinate normalizzate del dispositivo (normalized-device coordinates).

Successivamente, OpenGL utilizza i parametri di glViewport per mappare le coordinate normalizzate del dispositivo in coordinate dello schermo, dove ogni coordinata corrisponde a un punto del monitor

Questo processo è chiamato trasformazione del viewport (viewport transform).

in pratica il diagramma è

```scss
[Vertex Shader Output] 
        │
        ▼
   Clip-Space Coordinates
        │   (matrici di trasformazione)
        ▼
Perspective Division
        │
        ▼
Normalized Device Coordinates (NDC)
        │   (valori tra -1 e 1)
        ▼
Viewport Transform (glViewport)
        │
        ▼
Screen Coordinates (es. 800x600)

```