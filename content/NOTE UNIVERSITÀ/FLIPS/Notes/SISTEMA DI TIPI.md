#### Data: 09/10/2024 - 18:14

Il sistema di tipi serve per _"disciplinare"_ i programmi che scrivo con un linguaggio di programmazione. Viene usato per:
- descrivere quando i programmi hanno senso
- prevenire certi tipi di errori
- per strutturare programmi
- guidare il design del linguaggio
- fornire informazioni agli ottimizzatori dei compilatori
- rinforzare proprietà di sicurezza
Formalmente definiremo una relazione ternaria nel seguente modo
$$
\Gamma \vdash e : T
$$si legge _"L'espressione $e$ di tipo $T$ avendo assunto la premessa $\Gamma$ in cui sono presenti tipi di locazione che possono occorrere in $e$"_
Per esempio
![[Pasted image 20241009182917.png]]
I tipi esistenti per le espressioni nel linguaggio while sono:
$$
T::= int |bool|unit
$$Oltre ai primi due, $unit$ si riferisce ai tipi di comandi (es. Skip) 
Poi ci saranno i tipi per le locazioni:
$$
T_{loc} ::= intref 
$$ $intref$ sta per riferimento ad int
Ora vediamo le regole di inferenza per quanto riguarda $\Gamma \vdash e : T$

![[Pasted image 20241010144452.png]]
![[Pasted image 20241010144550.png]]
![[Pasted image 20241010144636.png]]
Ci sono diverse proprietà per quanto riguarda i tipi:
![[Pasted image 20241010145221.png]]
![[Pasted image 20241010145540.png]]
Ci sono due tipi di interferenza:
- Type checking problem 
	dato un tipo di sistema, un'ambiente di tipi $\Gamma$, un'espressione $e$ ed un tipo $T$, si può dedurre che $\Gamma \vdash$ $e : T$ ?   
- Type inference problem
	dato un tipo di sistema, un'ambiente di tipi $\Gamma$ ed un'espressione $e$ trovare un tipo $T$ tale che si può dedurre che $\Gamma \vdash$ $e : T$ , o mostrare che non ci sia 
Il secondo problema è molto più difficile del secondo perchè non ci viene dato a priori il tipo 