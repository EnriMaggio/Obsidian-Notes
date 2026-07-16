#### :LiCalendarClock:  15/10/2024 - 11:29

#### COME DEFINIRE I NUMERI NATURALI:
I numeri naturali possono essere definiti facilmente in questo modo:
- *CASO BASE*: 0 appartiene ad $N$
- *CASO INDUTTIVO*: se k (qualsiasi numero) appartiene ad $N$ allora il suo successore è naturale k + 1, quest'ultimo è definito da un numero più piccolo k 
Con queste due regole abbiamo costruito in modo induttivo l'insieme dei numeri naturali.
Ci possiamo applicare delle f a questo insieme naturale, ad esempio
$$
f: \mathbb{N} \rightarrow X
$$
è una funzione che preso un n appartenente ad N ci restituisce un elemento x appartenente ad X. Per fare induzione su questa f si fa:
- *CASO BASE*: descrivere che succede quando applico f(0)
- *CASO INDUTTIVO*: assumendo f(k) (ipotesi induttiva) definire f(k + 1) in termini di f(k)
#### INDUZIONE MATEMATICA:
E' una tecnica di dimostrazione usata per ==**dimostrare**== che una certa proposizione, teorema o proprietà è vera se il suo enunciato è formulato in funzione di ==**numeri naturali**== per tutti gli interi positivi o per una sequenza di valori naturali. In pratica _"dimostrare che per ogni $n \in N$ vale $P(n)$"_  (per $P(n)$ una qualsiasi proprietà che prende in input $n$)
Per farlo dobbiamo vedere se valgono le seguenti condizioni:
- *CASO BASE*:
	Si dimostra che la proposizione è vera per il primo caso, in genere $n$ = 0
- *CASO INDUTTIVO*:
	Si suppone che la proposizione ==**sia vera**== per un certo numero $n = k$, se $P(n)=true$ per $n=k$ (questa ipotesi è detta **ipotesi induttiva**) allora lo sarà anche per $n=k+1$. In sostanza si dimostrerà che $p(k) \Rightarrow p(k+1)$ 


Siccome non possiamo dimostrare manualmente per ogni caso (tempo e potenzialmente andando all'infinito), l'idea è quella di verificare per il caso base la proprietà, usando quest'ultima come base dobbiamo dimostrare il caso successivo usando il caso base e l'ipotesi induttiva 
Se questi due passaggi sono completati correttamente, possiamo concludere che la proposizione è vera per **ogni numero intero**. 


#### ESEMPI: 
![[IMG_0888.png]]

![[Pasted image 20241015175213.png]]
#### :LiExternalLink: REFERENZE:https://www.youtube.com/watch?v=GdM_iA1Zek4, https://www.youtube.com/watch?v=JTgWbq-S6Zc