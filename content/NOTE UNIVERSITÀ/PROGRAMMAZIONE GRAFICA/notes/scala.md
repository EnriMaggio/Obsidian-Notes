La **scalatura** è una trasformazione geometrica che modifica le **dimensioni di un oggetto** lungo uno o più assi.  
Non cambia la forma "topologica" dell'oggetto, ma può **ingrandirlo**, **rimpicciolirlo** o **deformarlo**.

il vettore in input viene moltiplicato per un fattore di scala, il risultato sarà il vettore riscalato di una certa grandezza

![[Pasted image 20250503111910.png]]

Ci sono 2 tipi di scalatura

1. **Scalatura uniforme**
    - Si usa **lo stesso fattore di scala** per tutti gli assi (es: x, y, z).
    - L’oggetto mantiene le **proporzioni originali**.
    - Esempio: un quadrato diventa un quadrato più grande o più piccolo.
2. **Scalatura non uniforme**
    - Si usano **fattori di scala diversi** per ogni asse.
    - L’oggetto viene **deformato**.
    - Esempio: un quadrato può diventare un rettangolo (allungato su un solo asse).

Con la matrice con coordinate omogenee invece diventa

![[Pasted image 20250503152623.png]]

![[Pasted image 20250503152732.png]]
bisogna tener conto che il fattore di scala va a modificare la distanza dall'origine

L'inversa della matrice di scala è la stessa matrice ma con le coordinate di scala invertite ovvero 1 diviso la coordinata

![[Pasted image 20250504121735.png]]