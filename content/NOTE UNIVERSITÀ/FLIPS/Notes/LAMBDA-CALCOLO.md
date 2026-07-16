#### :LiCalendarClock:  22/10/2024 - 12:15

#### Sistema formale

il $\lambda$ calcolo, creato da alonso church prima della macchina di turing, è Il dna della programmazione funzionale.

E un ==**sistema formale**== sviluppato per analizzare formalmente le ==**funzioni**== e il loro calcolo. In particolare è un modello computazionale che definisce il ==**calcolo**==, come la computazione deve essere svolta attraversi applicazione di sostituzione di funzioni

Sono le primitive delle funzioni (funzionano come black box) e non hanno stati, prendono in input dei valori e restituiscono l'output (senza sapere cosa fanno in realtà) a differenza della macchina di turing che i stati ce li ha e descrive passo passo come dall'input ottenere l'output (white box) 

il $\lambda$ calcolo è turing complete, poteva eseguire qualunque computazione espressa come algoritmo, infatti può essere visto come un semplice linguaggio di programmazione i cui le computazioni sono descritte come oggetti matematici
#### Differenze con Macchina di Turing

sia che $\lambda$ calcolo e macchina di turing arrivano allo stesso risultato di fronte al problema, ci arrivano in modi differenti comunque sono formalmente equivalenti.
Il primo userà un'approccio funzionale mentre il secondo adotta un'approccio sequenziale imperativo
![[Pasted image 20241022124707.png]]

#### Componenti del $\lambda$ calcolo
E un linguaggio formale dove ogni termine denota una funzione e ogni funzione può essere applicata ad ogni altra funzione ([[High Order]])

Ci sono tre elementi essenziali
![[Pasted image 20241022155547.png]]

Si può notare  che le funzioni $\lambda$ non contengono un nome che li identifica (a differenza delle funzioni) infatti sono dette anonime

Ecco un esempio di come si legge
![[Pasted image 20241022122812.png]]

in pratica
$$
(\lambda \text{ INPUT.OUTPUT) (ARGOMENTO FORMALE)}
$$
#### Come si valutano le funzioni

![[Pasted image 20241022161127.png]]
quando dobbiamo valutare un'oggetto M abbiamo due scelte
- CALL BY VALUE (eager)
	quando si valuterà M si andrà a prendere il valore dopo la valutazione di esso e in seguito quel valore andrà sostituito nella variabile d'interesse
- CALL BY NAME (lazy)
	qua invece al posto di valutare M con un valore, andremo a sostituire la variabile d'interesse con il nome di M, quindi M non viene valutato. Viene passato soltanto il nome
In base a come valutiamo può essere che il comportamento del nostro programma può variare, o meglio che alcuni aspetti attesi cambiamo in seguito a come abbiamo deciso di valutare i termini

La semantica di base per queste due valutazioni sono
![[Pasted image 20241022161949.png]]

Ora prendiamo un esempio di una espressione definita in [[FUNZIONI]] 

![[Pasted image 20241022164448.png]]
Questa $e$ è praticamente un comando sequenziale $e = e_1;e_2$

Adesso se provassimo a valutarla con cbv e cbn notiamo che questi due approcci restituiscono due situazioni differenti
- con cbv valutiamo $e1$ in una funzione $\text{fn x:T}\Rightarrow e$, poi valutiamo $e_2$ ad un valore $v$. In seguito sostituiamo il parametro attuale $v$ con il parametro formale $x$ nel corpo della funzione $e$ che poi andremo a valutare 
	![[Pasted image 20241022165303.png]]
- con cbn valutiamo $e_1$ in una funzione $\text{fn x:T}\Rightarrow e$, dopo sostituiamo l'argomento $e_2$ senza valutarlo nel parametro formale $x$ nel corpo della funzione (quindi $x = e_2$) e poi valutare $e$
	![[Pasted image 20241022165741.png]]
#### Funzione infinita

![[Pasted image 20241022164155.png]]

#### Semantica CBV small step semantics

![[Pasted image 20241022165913.png]]
#### Semantica CBN small step semantics

![[Pasted image 20241022170025.png]]

#### Type System

Il type system ci permette di capire se le funzioni sono fatte bene. Per il $\lambda$ calcolo il nostro ambiente in cui prima avevamo le locazioni, adesso avremo anche il tipo dei parametri formali
![[Pasted image 20241023180312.png]]

Sono separati perché non possiamo ancora astrarre i tipi locazioni.

Il tipaggio, essendo guidato dalla sintassi, avrà per ogni costrutto del linguaggio ($\lambda$) una regola per determinare bene il tipo della funzione

![[Pasted image 20241023181020.png]]

#### Proprietà del typing

Le proprietà di typing per questo linguaggio ha solo senso se non ci sono variabili libere

![[Pasted image 20241024141744.png]]

Spiegazione del lemma di sostituzione

![[Pasted image 20241024142351.png]]

#### Normalization

La Normalization può accadere o non accadere, in pratica dice che preso un programma tipato e se il programma è chiuso (no variabili libere), allora c'è un valore v ed uno stato s' in cui
$$
<e,s> \Rightarrow ^{*} <v,s> 
$$ Questo nel [[LINGUAGGIO-WHILE]] non è possibile, se si aggiungono questi tipi semplici al $\lambda$ calcolo, allora quest'ultimo perde il touring-complete (perchè con i tipi c'è solo convergenza)

#### :LiExternalLink: REFERENZE:https://www.youtube.com/watch?v=bm_s3VuDgAU, https://www.youtube.com/watch?v=eis11j_iGMs&t=3s, https://it.wikipedia.org/wiki/Lambda_calcolo 