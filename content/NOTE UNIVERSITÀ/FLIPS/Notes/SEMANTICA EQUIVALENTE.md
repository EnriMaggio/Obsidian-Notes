 #### :LiCalendarClock:  14/11/2024 - 21:22

#### Idea
Fino ad ora abbiamo dato una semantica operazionale, ovvero come evolvono i programmi a runtime

Ora possiamo dare una idea di semantica equivalente se dal punto di vista osservazionale se due programmi hanno lo stesso comportamento (avendo sintassi diversa e facendo percorsi diversi per arrivare allo stesso risultato)

Avere due programmi che hanno semantica equivalente per programmazione concorrente

#### Intuizione

Due programmi ad esempio $P_1$ e $P_2$ sono semanticamente equivalenti se $P_1$ può essere rimpiazzato da $P_2$ e viceversa.

$P_1$ e $P_2$ possono essere dei __moduli__ oppure delle __componenti__, cioè che se metto uno o l'altro in un contesto più grande, il contesto non cambierà il suo comportamento sia se scegliesse $P_1$ o $P_2$

![[Pasted image 20241114214615.png]]

ecco un esempio 

![[Pasted image 20241114215420.png]]

#### Cosa significa essere equivalenti

Le prime quattro proprietà possono fare la semantica equivalente ma non servono a nulla

l'obiettivo è quello di avere l'equivalenza semantica più ampia possibile
![[Pasted image 20241120104803.png]]

#### Contesto di un programma

il contesto di un programma è un programma non totalmente definito, cioè non ha alcune parti istanziate

![[Pasted image 20241120105445.png]]

#### Congruenze

I contesti spesso sono dei sistemi che hanno dimensione molto grande (aziende, fabbriche) quindi riscrivere un componente o un modulo per varie esigenze mantenendo la stessa semantica è al quanto infattibile. Inoltre se dovessimo verificare la equivalenza semantica dobbiamo avere a disposizione l'intero sistema, cosa che non succederà mai

Se l'equivalenza semantica è una congruenza allora si può stare tranquilli
![[Pasted image 20241120111555.png]]

#### Come si fanno le congruenze

Due programmi che hanno lo stesso tipo, sono equivalenti e dato qualsiasi store, se i due programmi dallo stesso store arrivano ad uno store modificato uguale, viene implicato l'uno per l'altro

![[Pasted image 20241120113805.png]]

se abbiamo due programmi semanticamente equivalenti ma arrivano alla fine con locazione diversa, i contesti distintivi sono contesti che se presi due programmi che sono diversi sono in grado di rendersi conto che c'è qualcosa di diverso

![[Pasted image 20241120114532.png]]

#### Regole generali

![[Pasted image 20241120114815.png]]
![[Pasted image 20241120114956.png]]
![[Pasted image 20241120115424.png]]

#### Simulazione e Bisimulazione

Siamo ancora con i programmi che vengono eseguiti sequenzialmente, in cui hanno informazioni mancanti (es temperatura captata da un sensore) che non riescono a coprire tutte le evoluzioni se non con il non determinismo

![[Pasted image 20241120123102.png]]
![[Pasted image 20241120123411.png]]

#### :LiExternalLink: REFERENZE: