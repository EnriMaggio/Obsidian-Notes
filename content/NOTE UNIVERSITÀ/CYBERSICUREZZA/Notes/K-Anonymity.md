#### Data: 05/02/2025 - 16:00

Il k-anonymity implica che i quasi-identifier di un record devono essere equivalenti ad almeno k-1 records. Per k intendiamo il numero di record minimo che una classe di equivalenza deve avere

![[Pasted image 20250205160933.png]]

Possiamo ottenere le classi di equivalenza con due metodi:
- **Generalizzazione:**
	sostituisce i valori degli attributi con valori più generici
- **Soppressione:**
	In alcuni casi, i record che non possono essere raggruppati per formare una classe di almeno k elementi vengono rimossi (operazione comune per gli outliers).

![[Pasted image 20250205161740.png]]
![[Pasted image 20250205161812.png]]
![[Pasted image 20250205161835.png]]
![[Pasted image 20250205161925.png]]
![[Pasted image 20250205161944.png]]
![[Pasted image 20250205162016.png]]

Comunque vada questa soluzione non è perfetta

- Protegge contro identificazioni dirette ma non contro deduzioni indirette. 
- Gli attacchi mostrano la necessità di diversificare i valori sensibili e considerare le conoscenze esterne.
  
  ==Homogeneity Attack (Attacco di Omogeneità)==
  Questo attacco si verifica quando tutti i record in una classe di equivalenza condividono lo stesso valore per l’attributo sensibile.
  ==Background Knowledge Attack (Attacco con Conoscenza di Base)==
  Questo attacco si verifica quando un attaccante utilizza conoscenze esterne o di dominio per restringere le possibilità e dedurre informazioni sensibili..

![[Pasted image 20250205162648.png]]
#### REFERENZE: