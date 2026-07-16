Il modello di illuminazione che stiamo costruendo funziona **solo in un dominio locale**, cioè **non tiene conto di sorgenti esterne** o **di riflessi da altri oggetti** presenti nella scena.

Nella realtà, la luce si comporta in modo più complesso: ci sono **sfumature e variazioni di colore** causate da riflessi, ombre morbide, rimbalzi multipli e occlusioni.  
Tutto questo rientra nella **illuminazione globale**, che mira a **simulare accuratamente la luce indiretta** e le **interazioni tra superfici**.

Al contrario, l’**ambient lighting** è una **semplice approssimazione locale**, che serve a simulare la luce indiretta creando un effetto globale:

- **Non considera la geometria della scena.**
- **Non tiene conto della posizione o distanza di altri oggetti.**
- **Si calcola per ogni punto indipendentemente**, senza simulare interazioni.
- **Non dipende dalla direzione dell’osservatore né della luce.**

È come se **aggiungessimo un colore di base a tutta la scena** per evitare che le parti non illuminate risultino completamente nere. In questo senso, l’illuminazione locale **simula una luce costante** sempre presente nella realtà, ma troppo complessa da calcolare con precisione

![[Pasted image 20250530100334.png]]
![[Pasted image 20250530100344.png]]

Si utilizza l’illuminazione locale **per semplicità e performance**, dato che è **molto più leggera** rispetto ad algoritmi complessi di illuminazione globale (come radiosity o path tracing).

![[Pasted image 20250530100138.png]]

---
### Computazione

Molto semplicemente:
$$
Iambient​=ka​⋅Ia
$$

- $Iambient$​: intensità della luce ambientale applicata al punto.
- $ka$: coefficiente di riflessione ambientale del colore del materiale (quanto "assorbe" o "riflette" la luce ambientale).
- $Ia​$​: intensità della luce ambientale globale nella scena (di solito un colore fisso tipo grigio o azzurro scuro).

Non dipende dalla normale del punto, né dalla posizione della luce. È costante per ogni punto della superficie.