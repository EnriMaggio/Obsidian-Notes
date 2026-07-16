#### Data: 20/02/2025 - 22:23

Gli avversari possono inviare email di **spearphishing con link malevoli** per ottenere accesso ai sistemi delle vittime.

Questo metodo serve a eludere i controlli di sicurezza che analizzano gli allegati delle email. Anche in questo caso, gli attaccanti possono usare tecniche di ingegneria sociale, fingendosi fonti affidabili.

L’email contiene un link che, accompagnato da un testo ingannevole, spinge l’utente a cliccarlo o copiarlo e incollarlo nel browser, facendo leva sull’**esecuzione da parte dell’utente**. Il sito web visitato può compromettere il browser tramite exploit o invitare l’utente a scaricare file dannosi (applicazioni, documenti, ZIP, eseguibili).

Gli avversari possono anche inserire link che interagiscono direttamente con il client di posta elettronica, come immagini incorporate progettate per sfruttare vulnerabilità nel sistema. Inoltre, possono usare link apparentemente innocui che sfruttano caratteri speciali per imitare siti web legittimi (**attacco IDN homograph**). Gli URL possono essere offuscati utilizzando trucchi del formato URL, come nomi host in formato numerico o esadecimale, e la rimozione automatica di testo prima del simbolo **"@"** (es. `hxxp://google.com@1157586937`).

Un'altra tecnica è il **consent phishing**, che sfrutta URL di richiesta OAuth 2.0. Se l’utente accetta, concede agli attaccanti l’accesso ai propri dati tramite **token di accesso alle applicazioni**, consentendo loro di eseguire azioni per conto della vittima tramite API.

Infine, i link malevoli possono mirare a **l’autenticazione dei dispositivi**, come il flusso di autorizzazione dei dispositivi OAuth 2.0. Conosciuto come **device code phishing**, l’attaccante invia un link che reindirizza la vittima a una pagina dannosa, inducendola a inserire un codice o credenziali per ottenere un token di accesso al dispositivo.
#### REFERENZE:

