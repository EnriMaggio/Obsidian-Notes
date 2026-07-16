#### Data: 07/02/2025 - 09:27

L'intuizione è quella di aggiungere rumore ai dati inseriti dall'utente, e questo può avvenire in due modi

- **Globale**
	il rumore viene aggiunto al dato nel database, in questo modo se ci sono delle query da parti di analisti, quest'ultimi riceveranno risultati con rumore (imprecisi)
	![[Pasted image 20250207093429.png]]
	![[Pasted image 20250207093621.png]] 
- **Locale**
	Viene aggiunto il rumore ai dati in locale, ovvero sul dispositivo dell'utente. Per l'analista cambia il fatto che riceverà dei risultati più peggiori rispetto con il globale
	![[Pasted image 20250207093834.png]]
	![[Pasted image 20250207094027.png]]
Un meccanismo di privacy differenziale ==garantisce che la probabilità di osservare un determinato output non cambi significativamente se un singolo record viene aggiunto o rimosso== dal dataset.

![[Pasted image 20250207094533.png]]


---
### Definizione normale

![[Pasted image 20250207094956.png]]
**Epsilon (ε)**:
	È il parametro di privacy che misura il livello di protezione. Valori più piccoli di ε indicano una maggiore privacy : è difficile distinguere i dati di un singolo individuo dal dataset.

![[Pasted image 20250207162519.png]]
![[Pasted image 20250207162551.png]]

---
### Sensibilità globale

la sensibilità di una query o di una funzione (in questo caso massimo) è dato dal massimo della differenza delle due query applicate ai due database $D$ e $D^{'}$ (che sono due database vicini, ovvero che differiscono per un solo elemento)
Ci dice di quanto è il cambio massimo della funzione per cui differiscono due database

![[Pasted image 20250207163252.png]]

---
### Global Sensitivity Method nella Privacy Differenziale

prendiamo per esempio questi due database
![[Pasted image 20250207163420.png]]
con due sensibilità
- cardinalità sul nome
	![[Pasted image 20250207163720.png]]
- media sugli anni ![[Pasted image 20250207163803.png]]
#### REFERENZE: