Il **Texture Mapping** è una tecnica della grafica 3D che consiste nell’applicare un'immagine (**texture**) a un oggetto tridimensionale per definirne l'aspetto visivo. Questo permette di aggiungere dettagli come colori, pattern e materiali senza aumentare il numero di poligoni del modello.

![[Pasted image 20250324135237.png]]

 **Esempio:** In un videogioco, invece di modellare ogni singolo mattone di un muro, si applica una **texture di mattoni** su un piano 3D, ottenendo un effetto realistico con meno risorse.

---

## **Passaggi del Texture Mapping**

1️⃣ **Creazione della Texture** 🎨

- Un’immagine 2D (JPG, PNG, TGA, etc.) viene preparata per essere applicata sull’oggetto.

2️⃣ **Mappatura UV** 🗺️

- La superficie 3D viene "srotolata" in uno spazio 2D per associare le coordinate dell’oggetto a quelle della texture.
- Ogni vertice ha coordinate **(U, V)** che corrispondono ai punti della texture.

3️⃣ **Rendering e Applicazione** 🖥️

- Il motore grafico calcola i colori dei pixel usando le coordinate UV e la texture.
- Viene usato il **Bilinear Filtering** per evitare scalettature e migliorare la qualità dell’immagine.

---

## Tipi di Texture Mapping

- [[UV Mapping]]
- Planar Mapping
- Spherical & Cylindrical Mapping
- Triplanar Mapping
- Procedural Mapping