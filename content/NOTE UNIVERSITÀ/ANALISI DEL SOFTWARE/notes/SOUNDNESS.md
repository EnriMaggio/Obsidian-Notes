#### Data: 08/10/2024 - 11:30

#### Tags: 

La soundness significa che pretendiamo che l'implicazione sia vera in caso ci sia la soddisfazione della proprietà, l'implicazione diventa
$$
\forall p \text{ analisi(p) = true}
\implies p \text{ soddisfa } \pi

$$
quindi se accettiamo che quando il programma p soddisfa la mia proprietà anche nella realtà, vuol dire che stiamo approssimando per difetto ovvero stiamo parlando di inaccuratezza pessimistica. Dove non posso dare una risposta precisa, si suppone che la proprietà non valga (ma la proprietà potrebbe valere!)
![[Pasted image 20241008114534.png]]
Quindi ho una risposta certa nella soddisfazione della proprietà, ma non posso dare con certezza se p soddisfa $\pi$ se l'analisi di p è falsa (cioè se p è falsa l'analizzatore può dare come risposta sia true che false)