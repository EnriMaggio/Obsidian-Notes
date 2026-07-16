#### :LiCalendarClock:  16/12/2024 - 09:40

andiamo a vedere come si trasferisce un calcolo dal dominio concreto a quello astratto, questo per dare risposte al dominio astratto per riuscire ad analizzare quello che vogliamo nel mondo concreto


---
#### Computazione astratta

Le operazioni che si effettuano sugli elementi del dominio concreto, le vogliamo trasferire sui corrispettivi elementi del dominio astratto

se abbiamo
$$
f:c\rightarrow c
$$ allora ci sarà
$$
f^{\#}:a\rightarrow a
$$ ![[Pasted image 20241216095225.png]]
Però in qualche modo $f$ ed $f^{\#}$ devono essere collegati e questo è possibile con la relazione di correttezza, il calcolo astratto è corretto se approssima la proprietà del calcolo concreto

![[Pasted image 20241216095754.png]]

in modo del tutto analogo possiamo caratterizzare la correttezza confrontando i risultati nel mondo concreto

![[Pasted image 20241216100354.png]]

Possiamo osservare che la funzione $f^{\#}$ è corretta se è più approssimata dalla ==best correct approximation di f== 

![[Pasted image 20241216101207.png]]
![[Pasted image 20241216101231.png]]

---
#### Soundness su chiusura

![[Pasted image 20241216102927.png]]
![[Pasted image 20241216102943.png]]

analogamente dalla concretizzazione

![[Pasted image 20241216103622.png]]
![[Pasted image 20241216104000.png]]

costruire una analisa statica nel framework dell'interpretazione astratta (ovvero mediante GI - uco) garantisce la correttezza del calcolo astratto. Otteniamo una analisi corretta per costruzione


---
#### Precisione

quando possiamo dire che una analisi è precisa? Quando il calcolo astratto restituisce un risultato essenzialmente uguale alla proprietà del calcolo concreto.

In sostanza quando quello che osserviamo non è rilevante per il calcolo
 ![[Pasted image 20241217103314.png]]
 Questo viene anche chiamato Backward Completeness
 ![[Pasted image 20241217103525.png]]

L'astrazione dell'input non causa perdita di informazione del calcolo

![[Pasted image 20241217103636.png]]
Questo viene anche detto completezza forward
Il significato del calcolo astratto coincide con il calcolo concreto

![[Pasted image 20241217103756.png]]

Osservare la proprietà del calcolo astratto non genera perdita di precisione 

[[esempi di completeness]]

La completezza è una proprietà del dominio astratto $p$ rispetto ad una operazione $f$

![[Pasted image 20241217111940.png]]


---
#### Trasferimento della semantica

Avendo
$$
F:C \rightarrow C
$$
$$
\alpha : C \rightarrow A 
$$ con GI tra $C$ e $A$

Vogliamo calcolare $\alpha$ (lfp $f$) senza calcolare lfp F perchè può divergere essendo sul concreto

Avviene quindi un trasferimento del punto fisso. Si cerca
$$
F:A \rightarrow A
$$ tale che lfp $F$ = $\alpha$ lfp $F$ 

Il punto fisso astratto deve essere uguale alla proprietà del punto fisso sul concreto

![[Pasted image 20241217113436.png]]

Il punto fisso astratto può avere problemi di terminazione 
#### :LiExternalLink: REFERENZE: