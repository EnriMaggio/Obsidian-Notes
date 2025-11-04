#### Data: 22/10/2024 - 10:08

Un ransomware è un tipo di [malware](https://www.ibm.com/it-it/topics/malware) che blocca (o meglio li cifra!) i dati sensibili o il dispositivo di una vittima, minacciando di tenerli bloccati, o peggio, a meno che la vittima non paghi un riscatto per la chiave di decriptazione.

I Ransomware contengono un Kill Switch che è una funzione, spesso nascosta, che consente di disattivare o arrestare il funzionamento del ransomware, interrompendone la diffusione o l'efficacia. È una sorta di "interruttore" che, una volta attivato, ferma il processo di cifratura dei file o annulla l'attività dannosa del ransomware.
### Caratteristiche del killswitch:

1. **Meccanismo di emergenza**: Il killswitch può essere inserito dai creatori del ransomware come una misura di emergenza o di controllo. Se i cybercriminali decidono di bloccare l’attacco o se vogliono mantenere una via d’uscita in caso di problemi, possono attivarlo per fermare il ransomware.
    
2. **Tipologie di killswitch**:
    - **Killswitch remoto**: Alcuni ransomware possono includere un meccanismo che consente agli hacker di disattivarli da remoto tramite un server di comando e controllo (C2). Se il server invia un comando specifico, il ransomware smette di funzionare.
    - **Killswitch locale**: Alcuni ransomware possono includere un controllo basato su condizioni locali, come la presenza di un file specifico, un dominio, o una certa configurazione nel sistema. Se questo elemento viene rilevato, il ransomware non esegue la cifratura o si disattiva automaticamente.

3. **Uso da parte dei ricercatori**: In alcuni casi, i ricercatori di sicurezza informatica scoprono un killswitch "accidentale" durante l'analisi del ransomware. Ad esempio, alcuni ransomware non cifrano i file se rilevano che il sistema è connesso a un dominio specifico o se trovano file di segnalazione, utilizzati come test. Un esempio famoso è il ransomware **WannaCry**, che conteneva un killswitch legato a un dominio web: quando un ricercatore ha accidentalmente registrato questo dominio, WannaCry ha smesso di infettare ulteriormente i sistemi, disattivando l'attacco globale.
    
4. **Funzione etica (rara)**: In casi rari, i creatori di ransomware possono includere un killswitch per smettere di colpire vittime specifiche o limitare l'area di diffusione del malware.

#### Cyber Kill Chain di un ransomware

![[Pasted image 20241022111208.png]]

#### Come comportarsi in caso di ransomware
![[Pasted image 20241022110848.png]]
#### REFERENZE: https://it.linkedin.com/pulse/wannacry-il-ransomware-20-spiegato-al-cybersecurity-summit-vaciago, https://www.youtube.com/watch?v=I5Wxh-rCzrY, ChatGpt :)