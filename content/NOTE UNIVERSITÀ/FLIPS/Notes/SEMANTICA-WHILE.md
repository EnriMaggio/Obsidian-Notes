#### Data: 09/10/2024 - 10:56
#### Linked Notes: [[SEMANTICA]],[[SMALL-STEP(EXP)]],[[STORE]]

La semantica operazionale per il while è definita in termini di ==**sistemi di transizione**== con un approccio small-step. Questi sistemi consistono in
- un insieme $\text{Config}$ di configurazioni
- relazione binaria $\rightarrow \subseteq \text{Config X Config}$
Gli elementi di $\text{Config}$ sono dette ==**configurazioni o stati**==, invece la relazione $\rightarrow$ è chiamata relazione di transizione o di riduzione. Si userà la notazione infissa per esprimere una transizione ad esempio
$$
c \rightarrow c' 
$$
questa transizione viene letta come "la configurazione c può fare una transizione/trasformazione per arrivare a c'"
##### <mark style="background: #FF000000; color:blue;">Configurazione</mark>
La configurazione $c$ non è altro che una coppia del tipo
$$
<e,s>
$$
 dove $e$ è una espressione ed $s$ una store. Le transizioni saranno nella forma
 $$
<e,s> \rightarrow <e',s'>
$$
dove $e'$ il risultato della valutazione dell'espressione. mentre $s'$ è il passaggio ad un nuovo stato (attenzione, può essere che non ci sia nessuna modifica allo stato ad esempio quando leggiamo da locazioni).
Si può interpretarla nel seguente modo _"Partendo da uno stato s e valutando l'espressione e, un passo di computazione porta ad uno store s' con l'espressione e′ che resta da essere valutata"_
##### Cosa è un passo
![[Pasted image 20241009114639.png]]
Nella penultima fase lo stato del programma (in memoria) cambia l'espressione valuterà $l=5$ e quindi si eseguirà la regola semantica dello store che assegna ad $l$ il numero $5$
##### <mark style="background: #FF000000; color:blue;">Regole di transizione del linguaggio while</mark>
- [[OPERAZIONI BASICHE]]
- [[DEREFERENZIAZIONE]]
- [[ASSEGNAMENTO]]
- [[CONDIZIONALE]]
- [[COMPUTAZIONE SEQUENZIALE]]
- [[CICLO WHILE]]