
### Data: 05/02/2025 - 15:24

Solitamente nelle nostre analisi ==bisogna affidarsi a dataset con informazioni sensibili personali ad utenti==. Come posso utilizzare questi dataset sfruttando le informazioni ma preservando la privacy degli individui?

![[Pasted image 20250205152626.png]]

Se non ==anonimizziamo== i dati in un dataset si rischia che un attaccante riesca a risalire alle informazioni personali e identità degli utenti

---
### ANONIMIZZAZIONE

E una tecnica di trasformazione che altera i dati in una maniera che un soggetto non possa essere rintracciato dai dati alterati in modo diretto o indiretto.

Per farlo prima dobbiamo classificare gli attributi presenti in un dataset
#### Explicit identifiers (Identificatori espliciti)
  Sono attributi che ==identificano direttamente l'individuo==.
	  - nome
	  - cognome
	  - numero di passaporto / CI 
	  - codice fiscale
	  - ...
  
- #### Quasi-identifiers (Quasi identificatori)
   Attributi che, presi ==singolarmente==, ==non identificano== un individuo, ma che possono essere ==combinati per rivelare l’identità==.
	  - data di nascita
	  - CAP
	  - numero di telefono
	  - ...
  
- #### Sensitive attributes (Attributi sensibili)
  Attributi che contengono ==informazioni personali critiche==.
  Sono il focus principale di analisi per i ricercatori o le aziende, rappresentando il valore informativo del dataset, devono essere quindi protetti senza compromettere l’utilità del dato.
	  - malattie
	  - salari
	  - opinioni politiche
	  - ...

ad esempio
![[Pasted image 20250205154052.png]]


---
#### Mititgazione al problema della privacy nei dataset

Per anonimizzare ci sono diverse tecniche, ma di base si fanno due operazioni fondamentali

- **Tokenization (Tokenizzazione) :** Genera un token univoco (un identificativo casuale) che sostituisce l’attributo originale.
	![[Pasted image 20250205155320.png]]
- **Substitution (Sostituzione):** Sostituisce un valore di attributo con un altro valore alternativo, spesso preso da un database predefinito.

Varie tecniche di anonimizzazione
- [[K-Anonymity]]
- [[L-Diversity]]
- [[T-Closeness]]


Ovviamente questo non basta per rendere automaticamente sicuro il dataset. Ci possono essere casi in cui si può risalire all'identità cercando collegamenti esterni tra documenti diversi

![[Pasted image 20250205155612.png]]


---
### ALTRO APPROCCIO

invece che utilizzare i dati direttamente si utilizzano risultati di analisi statistica (media, mediana, conteggi, ...).
Sebbene si tenda a pensare che le medie o i conteggi siano **anonimi**, nella pratica:
- **Analisi statistiche** possono rivelare informazioni sensibili individuali se non implementate correttamente.
- Gli attacchi di correlazione e inferenza dimostrano che anche dataset aggregati possono essere vulnerabili.
![[IMG_C007A8DD23BE-1.jpeg]]


---
### RECONSTRUCTION ATTACK

E un tipo di attacco che mira a ricostruire un dataset privato partendo da informazioni pubbliche aggregate. L'attaccante ha a disposizione niente oppure un accesso parziale al dataset privato, d'altra parte ha accesso alle statistiche pubbliche di quei dataset (che possono essere esatte o distorte)

Per attuare questo attacco, l'attaccante ha a disposizione le query
- Query aggregate (es. “Quanti uomini hanno una malattia?”) sono generalmente sicure, ma…
- Query mirate o combinate possono portare a deduzioni precise su individui specifici.
Ad esempio, inserendo un nuovo record nel database, come nella slide, è possibile dedurre l’età e il peso del nuovo record.

![[Pasted image 20250206090741.png]]

Ad esempio, inserendo un nuovo record nel database, come nella slide, è possibile dedurre l’età e il peso del nuovo record.
![[Pasted image 20250206090912.png]]
Anche limitando le query a quelle aggregate, si può comunque compromettere la privacy degli individui:

- Query troppo specifiche possono ridurre i risultati aggregati a un solo individuo o a un piccolo sottoinsieme, rivelando così informazioni sensibili.
- Questo mette in evidenza come le restrizioni sulle query non siano una soluzione definitiva.

La soluzione finale è la [[differential privacy]]

#### REFERENZE: https://www.youtube.com/watch?v=Q0DNOIGUzMc, https://en.wikipedia.org/wiki/Reconstruction_attack