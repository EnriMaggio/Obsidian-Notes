Abbiamo già visto che ci sono più diversi sistemi di riferimento in cui i punti e i vettori possono essere computati in base alle esigenze.

Quando trattiamo vettori e punti del lighting dobbiamo fare in modo che i vettori e operazioni in questione avvengono nello stesso sistema di coordinate

Immagina che tu stia calcolando il Phong shading:

```
float diffuse = max(dot(normal, lightDir), 0.0);
```

Questa operazione ha senso solo se normal e lightDir sono nello stesso spazio. Se la normal è in **object space** e la direzione della luce è in **world space**, allora:

 Il prodotto scalare non rappresenta il vero angolo tra i due vettori → lo shading sarà **sbagliato**.

Il sistema di riferimento preferito per applicare lo shading della luce [[spazio vista]], questo perché ci serve per calcolare con semplicità la riflettanza, non solo siccome lo spazio vista include la camera, il vettore vista è direzionata verso la camera.

L'importante prima di fare le trasformazioni è quella di portare tutti i vettori definiti magari in diversi spazi nello stesso sistema di riferimento

Però cambiare il sistema di coordinate potrebbe cambiare le orientazioni delle normali delle superfici

![[Pasted image 20250530120032.png]]
(questo non accade con le matrici di rotazione)

Per correggere bisogna applicare l'inversa della trasformazione applicata sulle normali per poi normalizzarle

Con trasformazioni che sono uniformi allora si può utilizzare la seguente formula

![[Pasted image 20250530120704.png]]

invece per la trasformazioni non uniformi dobbiamo modificare leggermente la matrice M 3x3

![[Pasted image 20250530121137.png]]
![[Pasted image 20250530121209.png]]