Una volta visto gli elementi di base della programmazione grafica, andiamo a vedere nel concreto quello che fa una GPU quando la CPU fornisce un frame, degli oggetti 3D che la scheda grafica dovrà occuparsi di tutto il Rendering.

![[Pasted image 20250324142643.png]]

A livello alto quello che succede è che partendo dal mondo che è espresso in un mondo tridimensionale noi andremo a fare le seguenti fasi

1. Modelling
	porta gli oggetti nella scena nel sistema di riferimento mondo
2. Camera 
	dobbiamo determinare il punto di vista con cui vedremo la scena, quindi i riferimenti del mondo passano a riferimenti della camera
3. Projection
	qui è dove si lascia il mondo tridimensionale, che verrà schiacciato sul mondo bidimensionale, e quindi si proietta quello che la camera vede su un piano, 
4. Viewport
	è la fase finale in cui si genera l'immagine finale colorando i pixel, definendo prima una griglia $m$ x $n$

Alla fine otteniamo difatti un'immagine renderizzata

Questa linea coinvolge [[sistema di coordinate]]