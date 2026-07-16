Con il **lighting** si riferisce all'insieme di tecniche utilizzate per simulare l'effetto della luce sugli oggetti tridimensionali in una scena virtuale. L'obiettivo è rendere la scena il più possibile realistica o visivamente interessante, riproducendo fenomeni come l'illuminazione direzionale, le ombre, i riflessi e le variazioni di colore dovute alla luce.

La luce fa quindi parte del rendering, perchè la resa grafica ne tiene conto.

Per determinare la luce abbiamo bisogno di:
- da dove arriva
- quantità di luce
- colore della luce
- osservatore che guarda la luce 

quindi in input abbiamo:

- caratteristiche dell'oggetto illuminato ("materiale"), questo perchè ogni oggetto reagisce in modo differente con la luce in base al suo materiale intrinseco
- caratteristiche della luce che illumina (dove, fonti)
- forma degli oggetti della scena, ovvero sapere gli orientamenti delle superfici rispetto alle sorgenti di luce

e in output abbiamo
- il colore percepito per un dato punto


Cerchiamo di capire quale interazione avviene tra sorgenti di luce e oggetti della scena

![[Pasted image 20250516114138.png]]

#### 1. **Sorgenti luminose**

- **LUCE** e **ALTRA LUCE**: rappresentano le fonti di luce nella scena.
- I raggi provenienti da queste luci si chiamano **raggi incidenti** (vettori che colpiscono la superficie).

#### 2. **Interazione tra luce e oggetto**

Quando la luce colpisce l'**OGGETTO**, possono succedere diversi fenomeni fisici:

- 🔴 **Riflessione**: parte della luce viene riflessa dalla superficie. È quella che di solito arriva all’occhio.
    
- 🟡 **Assorbimento**: parte dell'energia luminosa viene assorbita dall’oggetto, contribuendo al suo colore.
    
- 🟢 **Trasmissione con rifrazione**: la luce attraversa l’oggetto ma cambia direzione all'interno per poi uscire dall'oggetto stesso(es. vetro, acqua).
    
- 🟢 **Riflessione interna**: se il materiale è trasparente, la luce può rimbalzare all’interno.
    
- 🔵 **Scattering sotto la superficie**: la luce entra nella superficie e viene diffusa internamente (tipico di pelle, cera, latte...).
    
- 🌫️ **Assorbimento nel mezzo**: fenomeni atmosferici (come nebbia o fumo) possono ridurre la quantità di luce che arriva all’occhio o nel nostro caso una camera.
#### 3. **Blocchi e ombre**

- Un **blocker** può ostruire la luce e generare **ombre** su parti dell’oggetto, influenzando il lighting visibile.

#### 4. **Occhio / osservatore**

- L’**occhio** rappresenta l’osservatore o la camera in una scena grafica.
- L’unica luce che conta per il rendering finale è quella che riesce ad arrivare all’occhio dopo tutti questi fenomeni.