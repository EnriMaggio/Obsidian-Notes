# Report Progetto: Path Inference Attack via CAN Bus

Questo report documenta le metodologie, le scelte implementative e i risultati del progetto svolto per il corso di Network Security, ispirato al paper *"Your Car Tells Me Where You Drove: A Novel Path Inference Attack via CAN Bus and OBD-II Data"* (VehicleSec 2025). Il lavoro è diviso in 8 capitoli, strutturati per una presentazione bilanciata a due voci.

## Struttura della Presentazione (8 Capitoli)
1. **Capitolo 1: Introduzione e Threat Model** (Presenter A)
2. **Capitolo 2: Il Dataset CANdid e Component Identification** (Presenter A)
3. **Capitolo 3: Ground Truth Engineering: Mappe Cartografiche vs. GPS Bearing** (Presenter A)
4. **Capitolo 4: Selezione delle Feature e Verifica dello Sterzo** (Presenter A)
5. **Capitolo 5: Architetture dei Modelli di Machine Learning** (Presenter B)
6. **Capitolo 6: Strategia di Training e Cross-Validation Stratificata** (Presenter B)
7. **Capitolo 7: Risultati Sperimentali e Analisi Comparativa** (Presenter B)
8. **Capitolo 8: Ottimizzazioni Software, Trasferibilità e Conclusione** (Presenter B)

---

## PARTE 1: Contesto, Dataset e Pre-processing (Presenter A)

### Capitolo 1: Introduzione e Threat Model
Il bus CAN (Controller Area Network) è lo standard di comunicazione interno ai veicoli. Poiché le comunicazioni non sono nativamente crittografate o autenticate, esse risultano intrinsecamente vulnerabili. Tramite la porta diagnostica standardizzata OBD-II, è possibile estrarre i dati di rete ad alta velocità.
Il nostro *threat model* prevede un attaccante passivo che registra il traffico CAN tramite un dongle commerciale OBD-II o manomettendo dispositivi esposti (ad esempio i fari esterni). L'obiettivo è ricostruire il percorso, i pattern di accelerazione e le abitudini del guidatore (path inference attack) usando modelli di machine learning che elaborano esclusivamente messaggi CAN, senza l'ausilio di sensori GPS, sollevando di fatto gravi implicazioni per la privacy.

### Capitolo 2: Il Dataset CANdid e Component Identification
Il progetto sfrutta il **CANdid Dataset**, che include registrazioni di 10 veicoli in scenari reali e diversificati ("driving captures") e test controllati da fermo ("control captures"). A differenza della maggior parte dei dataset precedenti, che sono focalizzati prevalentemente sui cyber-attacchi (injection, fuzzing), CANdid fornisce label precise delle azioni del guidatore e log GPS.
Per identificare il segnale dello sterzo senza disporre dei file proprietari DBC per decodificare il payload, è stata utilizzata la statistica TANG (tasso di transizione dei bit) misurata sulle control captures. Tale statistica è stata poi correlata alle annotazioni temporali degli inserimenti con il coefficiente di correlazione **Punto-Biseriale** (equivalente matematicamente a una matrice di Pearson). Il CAN ID e i bit con punteggio massimo sono stati isolati per tracciare accuratamente i movimenti del volante da inserire nei modelli inferenziali.

### Capitolo 3: Ground Truth Engineering: Mappe Cartografiche vs. GPS Bearing
A differenza del paper originale, che faceva affidamento su mappe cartografiche avanzate per etichettare solo le svolte in netta corrispondenza degli incroci (classificando così solo il 12% dei casi come positivi), il nostro approccio ha ricostruito i percorsi in assenza di ground-truth usando le API di *OpenStreetMap* via *Folium*.
Non potendo utilizzare direttamente il campo `Heading` (poiché pesantemente smorzato dal firmware del ricevitore GPS hardware, rendendo le svolte "invisibili" temporalmente), abbiamo calcolato la direzione reale tramite la **formula dell'azimut sferico** direttamente dalle coordinate grezze di latitudine e longitudine:
$$
x = \sin(\Delta lon) \cdot \cos(lat_2)
$$
$$
y = \cos(lat_1) \cdot \sin(lat_2) - \sin(lat_1) \cdot \cos(lat_2) \cdot \cos(\Delta lon)
$$
$$
bearing = \text{atan2}(x, y)
$$
Abbiamo calcolato il *NetBearing* (la variazione angolare netta accumulata su una finestra di 20 secondi) applicando una soglia geometrica (≥30°) e un filtro di velocità minima (≥10 km/h) per eliminare il rumore GPS stazionario. Questo metodo matematico rileva anche le curve stradali prolungate e le rotatorie, portando la percentuale di campioni "turning" (svolta) al 26%.

### Capitolo 4: Selezione delle Feature e Verifica dello Sterzo
Per ragioni prestazionali e computazionali, rispetto al paper originale che utilizzava $N_f = 82$ CAN ID completi contemporaneamente, il nostro progetto seleziona solamente i $N_f = 10$ ID più rilevanti. Questa estrazione avviene valutando il ranking Punto-Biseriale rispetto alla curva stimata dal GPS.
Inoltre, per risolvere una severa criticità analitica legata al modello single-feature ($N_f = 1$), abbiamo introdotto una verifica forte del CAN ID storicamente associato allo sterzo. Invece di fidarci di un ID auto-rilevato, abbiamo elaborato la control capture dello sterzo con la statistica TANG e isolato in modo deterministico l'ID esatto, forzandolo all'interno dei modelli di guida. Questo processo metodologico garantisce che le feature del modello $N_f = 1$ rappresentino in modo inequivocabile i movimenti del volante.

---

## PARTE 2: Modelli, Valutazione e Ottimizzazioni (Presenter B)

### Capitolo 5: Architetture dei Modelli di Machine Learning
I modelli neurali elaborano finestre mobili sequenziali di $N_w = 100$ messaggi, accuratamente raggruppate e impilate per ogni CAN ID. Sono state sviluppate e testate due architetture in PyTorch:
1. **SharedANN (Artificial Neural Network)**: Una rete completamente densa a 3 layer, configurata affinché i pesi topologici del primo layer siano condivisi equamente (Shared) per tutti i CAN ID in fase di estrazione bidimensionale, prima dell'appiattimento (flattening).
2. **SharedCNN (Convolutional Neural Network)**: Una rete avanzata in cui due layer convoluzionali paralleli operano indipendentemente ed esclusivamente su ogni CAN ID prima della fusione nei fully-connected layer. 
Entrambe le reti operano come classificatori binari (0 = rettilineo, 1 = svolta) utilizzando la metrica di *Binary Cross-Entropy Loss (BCE)*, integrata con pesi dinamici per bilanciare l'asimmetria delle classi.

### Capitolo 6: Strategia di Training e Cross-Validation Stratificata
L'approccio del paper adottava uno split puramente cronologico (75/15/10). Questo schema è analiticamente sfavorevole e porta a metriche falsate: il test set si limitava a valutare le ultime quattro svolte finali del percorso, causando un grave *distribution shift* (18% positivi nel train contro il 62% di densità nel test).
Per garantire una validazione scientifica inoppugnabile, abbiamo implementato una solida **K-Fold Cross-Validation Stratificata a Blocchi** (con K=5). L'intera cattura è stata divisa in 40 blocchi, ordinati per percentuale di ratei positivi (`pos_rate`) e distribuiti tramite partizioni uniformi nei set 60/20/20.
Il coefficiente per bilanciare la *Loss* è calcolato strettamente in isolamento sul training set di ogni specifico fold (`pos_weight = n_neg/n_pos`).
Per contrastare vigorosamente l'overfitting, le 500 epoche fisse usate dai ricercatori di USENIX sono state rimpiazzate da una struttura regolarizzata con dropout (0.5), weight decay (1e-3) e tecnica di *Early Stopping* con patience.

### Capitolo 7: Risultati Sperimentali e Analisi Comparativa
Valutando le predizioni sulla vettura 5 tramite le curve ROC-AUC:
*   **ANN $N_f = 10$:** 0.8513 ± 0.0480 (Rispetto a 0.913 nel paper)
*   **CNN $N_f = 10$:** 0.8720 ± 0.0334 (Rispetto a 0.931 nel paper)
*   **ANN $N_f = 1$ (Sterzo Verificato):** 0.6510 ± 0.0584 (Contro lo 0.953 del paper)

I risultati del nostro ecosistema multi-variato ($N_f = 10$) risultano solidi e comparabili, ancor di più considerando che le etichette coprono l'interezza del percorso (inclusi incroci lunghi ed ambigui) e superano uno stress test in 5-fold CV.
La drammatica flessione delle performance nel modello $N_f = 1$ è scientificamente giustificata. Poiché le etichette di NetBearing marcano curve molto ampie ed estese nel tempo, il volante fisico all'interno della vettura rimane spesso stazionario. Di conseguenza, il modello neural single-feature subisce forte *underfitting* (loss alta in training) contraddicendo l'etichetta GPS. I modelli multi-feature compensano con estrema efficacia estrapolando dati sinergici dall'imbardata, dalle ruote e dalla velocità longitudinale.

### Capitolo 8: Ottimizzazioni Software, Trasferibilità e Conclusione
Il codice base è stato pesantemente **ottimizzato** e re-ingegnerizzato:
*   *Parsing CAN Vettorizzato*: L'estrazione hardware bit-a-bit su liste lente è stata soppressa a favore di `bytes.fromhex` e `np.unpackbits` vettoriali, abbattendo i tempi di 50x.
*   *Estrazione Feature "Lazy"*: Per aggirare enormi saturazioni di memoria (oltre 6GB per le matrici a 4 dimensioni), vengono caricati on-the-fly soltanto gli indici limite dei CAN ID per la generazione batch.
*   *Computazioni $O(n \log n)$*: NetBearing indicizzato via interpolazione binaria di ricerca anziché doppio loop temporale quadratico.
Infine, un massiccio esperimento per estendere l'architettura a uno scenario cross-vehicle LOCO (addestramento su un modello di vettura e test su un altro) ha svelato profonde limitazioni: a causa della semantica CAN proprietaria (CAN ID hex incompatibili) l'inferenza raw decade a valori casuali (AUC ~0.50), ponendo le basi per architetture basate su metriche Z-score di flip-rate statistici come prossimo step di astrazione.

**Conclusione**: L'infrastruttura ingegnerizzata dimostra robustamente le potenzialità di tracciamento invasivo via CAN bus, colmando al contempo numerose falle di generalizzazione e overfitting rilevate nel paper originario.
