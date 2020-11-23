
# VALUTAZIONE

## LINEE GUIDA
- I documenti vanno consegnati come una cartella radice che contiene le varie parti, separate opportunamente per natura (interni, esterni) e funzione (tecnici, gestionali).
- I riferimenti vanno sempre suddivisi fra informativi e normativi e uno stesso riferimento non può appartenere ad entrambe le categorie.
- I verbali e il capitolato sono tipicamente riferimenti normativi.
- Nei documenti dotati di struttura chiara (per organizzazione delle parti e loro titoli) non serve introdurre ogni parte dicendo di cosa si occupa.
- Non va usato il tempo futuro per riferirsi a contenuti esistenti nel tempo presente.
- Se si avanza di versione dopo una modifica senza che essa sia stata verificata si rischia iterazione.
- Il registro delle modifiche va posto in testa al documento, prima dell'indice dei contenuti.
- Nel registro delle modifiche vanno forniti dettagli sulla storia delle versioni, non delle singole azioni.
- Attribuire molte azioni temporalmente distinte allo stesso numero di versione causa confusione.
- Il luogo di modifica va riferito numericamente invece che per nome, usando il simbolo “§n” per designare la parte ‘n’ del documento.
- L’eventuale indirizzo di una risorsa digitale all’interno di una voce bibliografica non deve essere nascosto dietro un link, ma completamente visibile.
- Nel nome dei documenti la data andrà riportata nel formato AAAA-MM-GG.
- Il nome dei documenti ne deve riportare il numero di versione.
- Applicare regola "need to know": la logica di distribuzione dei prodotti (anche documenti) deve coinvolgere solo i diretti interessati.
- I riferimenti sono utili se specifici e localizzabili.
- Un intero libro o una collezione (per esempio diapositive) sono troppo vasti per essere riferimenti utili quindi ne va specificata la parte di interesse.
- Se ci si riferisce a documenti che hanno un ciclo di vita bisogna riportarne la versione o l'edizione (per i libri).
- Attenzione alle iniziali maiuscole usate nei titoli delle parti di documento, devono essere corrette e consistenti.
- Evitare di mettere riferimenti a pedice dei titoli.
- La versione del documento va riportata in ogni sua pagina.
- Preferire allineamento “giustificato” per il testo.
- E' desiderabile che i PDF includano bookmark.
- In espressioni come "il fine di ... è quello di" "quello di" è ridondante.
- E' opportuno che il piè di pagina riporti anche il numero totale di pagine del documento.
- Attenzione alla qualità ortografica.
- Usare la denominazione corretta degli standard.
- Wikipedia non è sempre fonte sufficientemente autorevole. Più di essa lo sono le fonti bibliografiche cui si riferiscono le corrispondenti voci.

## LETTERA DI PRESENTAZIONE
- Di norma la prima comunicazione con la quale il fornitore candidato si presenta al committente include in allegato la propria composizione e i ruoli correnti.
- I documenti non si post-datano. Non puoi associare a un documento una data successiva a quella di consegna.
- Il prezzo dichiarato deve stare nei limiti.

## NORME DI PROGETTO
- Gli standard 15504 e 25010 non vanno assunti come normativi perchè sarebbe troppo oneroso.
- Lo standard ISO/IEC 12207 si istanzia e non si adotta in quanto tale.
- E' meglio considerare ISO 8601 come riferimento informativo, non come norma.
- Le attività del processo di fornitura includono anche gli incontri con il proponente e la loro verbalizzazione, che devono essere normati.
- Meglio associare le metriche alle attività a cui si applicano e alle corrispondenti procedure.
- Attenzione a normare esaustivamente l'attività di progettazione.
- Tra i processi di supporto va considerato anche il processo di gestione dei cambiamenti.
- Tra i processi organizzativi è utile considerare il processo di formazione.
- La struttura canonica del documento è: categoria di processi -> processo specifico -> suoi obiettivi (inclusi quelli qualitativi), attività, procedure e strumenti di supporto.
- Attenzione a considerare tutti i processi. Spesso si dimentica il processo dei rapporti col proponente.
- Non includere PdP o PdQ tra i riferimenti informativi se no si crea circolarità. Le Norme dovrebbero essere una premessa alla redazione di qualunque altro documento.
- Nella normazione della progettazione sono state incluse attività che non le appartengono, come PoC e test.
- Formulazione delle norme non deve essere narrativo e superficiale. Deve contenere passi procedurali e di riferimento operativo alle tecnologie adottate per supportare il lavoro.
- Non va bene che la copertura dei processi attivati nel progetto sia più in ampiezza che in profondità.
- La progettazione non deve essere parte dell'analisi.
- Attribuire i processi alle tre categorie principali in modo corretto.
- La codifica è un'attività del processo di sviluppo, non un processo.
- Le norme sono destinate ai ruoli e non agli individui.

## ANALISI DEI REQUISITI
- AWS Lambda non è un attore esterno, poiché le funzioni eseguite nel contesto di Amazon fanno parte del sistema.
- Il broker (Kafka) fa parte del prodotto, come anche il database, pertanto non dovrebbe essere annoverato tra gli attori.
- Deve esserci tracciamento tra casi d'uso e requisiti.
- I casi d'uso vanno suddivisi correttamente.
- La suddivisione va fatta  per casi d'uso e non per moduli.
- Nell'Analisi dei Requisiti ci vanno le funzionalità, non i dettagli implementativi.
- La descrizione e lo scenario principale devono essere inseriti in ogni caso d’uso, per quanto triviali esse siano.
- L’inclusione non può essere utilizzata per modellare pre-condizioni o flussi temporali fra casi d’uso.
- La versione approvata dal responsabile deve essere quella consegnata.
- Un diagramma dei casi d’uso di per sé rappresenta un caso d’uso, e come tale necessita di descrizione.
- L'attore principale di un caso d'uso dev'essere chiaro.
- Un caso d'uso non può essere presente nel proprio diagramma dei casi d'uso.
- A volte casi d'uso sono troppo eterogenei per comparire nello stesso diagramma dei casi d'uso.
- Nella tabella dei requisiti doverbbe essere riportato a quale caso d'uso il requisito faccia riferimento.
- Ogni diagramma dei casi d’uso deve essere associato a un caso d’uso.
- Mostrare le relazioni tra i vari attori.
- “Requisiti dichiarativi” -> “Requisiti di Vincolo”

## STUDIO DI FATTIBILITÀ
- Il capitolato scelto dovrebbe essere approfondito più degli altri.

## PIANO DI PROGETTO
- Se si aderisce al modello incrementale bisogna occuparsi anche dello sviluppo degli incrementi, non concentrarsi solo sui documenti e sulle revisioni di avanzamento, altrimenti si destituiscono pianificazione temporale e preventivo economico.
- Conviene che ai rischi individuati (e alle corrispondenti contromisure) venga associato un codice mnemonico che ne faciliti il riferimento.
- In una struttura paritaria (per conoscenze e abilità) come la nostra non è ragionevole far valutare al responsabile conoscenze e abilità. E' meglio che ognuno si auto-valuti e segnali difficoltà o lacune.
Più che all’assistenza reciproca, la corrispondente contromisura dovrebbe puntare alla condivisione strutturata e persistente dell’informazione.
- Non fare monitoraggio "attivo"/polling. Meglio tecniche proattive. Fornire al responsabile un cruscotto informativo, collegato con le azioni assegnate e le loro scadenze, idealmente capace di ricordare le scadenze imminenti e quelle arrivate.
- Prima dell'ingresso in RA non c'è "Consuntivo" ma "Consuntivo di periodo".
- Prima della RR per il committente non c'è "preventivo a finire" ma "preventivo".
- Il consuntivo di periodo serve per ragionare, in corso d’opera, sulle ragioni degli scostamenti rilevati, sulle loro possibili mitigazioni, e sui conseguenti raffinamenti di pianificazione da effettuare nei periodi successivi, da riflettere poi nel “Preventivo a finire”.
- L'analisi dei rischi è attività dinamica e vigilante per l'intera durata del progetto, pertanto ai contenuti che riportate deve corrispondere una loro attualizzazione che ne discuta l'occorrenza e la mitigazione nel periodo osservato ed effettui il raffinamento dell'analisi a valle di quanto eventualmente avvenuto e appreso.
- L'attualizzazione dell'analisi dei rischi è meglio collocata in appendice.
- Sul piano logico l'analisi dei rischi viene prima del modello di sviluppo e della pianificazione.
- Gli incrementi previsti si devono riflettere sulla pianificazione.
- Il preventivo dovrebbe avere relazione con gli incrementi.
- Vi è differenza tra “modifica” e “incremento”.
- Computare unità di tempo inferiori all’ora è più un eccesso di zelo che una misura utile.

## PIANO DI QUALIFICA
- Il PdQ deve essere integrato con le Norme. Queste ultime devono fissare metriche e strumenti per misurarle mentre il PdQ deve fissare gli obiettivi quantitativi di qualità del progetto.
- Il resoconto delle attività di verifica (che devono riflettere tutte le metriche adottate) è meglio presentato con serie storiche e diagrammi a contenuto incrementale, invece che tramite tabelle che “fotografano” gli eventi,ma non li mettono in relazione tra loro, oppure, peggio, tramite riferimento ad altre fonti informative.
- Anche la verifica tramite test va associata a obiettivi metrici (per esempio i vari fattori di copertura)
- E' eccessivamente ambizioso e quindi troppo oneroso assumere gli standard 9126 e 12207 come normativi.
- Per lo standard 9126 è meglio derubricarlo a riferimento informativo, traendo da esso solo le parti di stretto e applicabile interesse.
- Ogni obiettivo metrico dichiarato è oggetto di verifica sistematica, assai più frequente delle revisioni previste dal bando.
- Rimandare senza scadenza non è professionale.

## GLOSSARIO
- Meglio separare i gruppi alfabetici delle voci riportate, iniziando ogni nuovo gruppo da pagina nuova.
- Meglio che l’indice dei contenuti non includa tutte le voci del glossario: basterà limitarsi ai loro gruppi.
- A questo tipo di documento, la cui funzione è auto-esplicativa, e la struttura auto-evidente, non serve introduzione, se non per dichiarare con precisione le fonti consultate per le definizioni fornite.

## VERBALI
- Le decisioni riportare nelle tabelle riassuntive devono essere precise, non ambigue o incomplete. Se non si può scrivere la decisione nel verbale bisogna fare un riferimento a una fonte esterna che la descriva.
- Il compito principale di un verbale è fare memoria delle decisioni prese per affrontare situazioni emergenti. Quindi la parte più importante di esso è un riepilogo tracciabile delle decisioni prese.
- Un solo verbale esterno segnala insufficiente interazione col proponente.
- Il nome del documento deve comprendere la data di svolgimento della riunione.
- Il nome del verbale deve distinguere tra interno ed esterno.
- Scegliere il codice assegnato alle decisioni in modo che non causi sovrapposizione di riferimento.
- Gli incontri hanno una data, un luogo, un orario di inizio e di fine, e dei partecipanti e i verbali devono includere queste informazioni.
- I verbali esterni e interni vanno raccolti in cartelle separate.
- I verbali interni non sono destinati al committente, ma solo offerti in visione, per ragioni di trasparenza.

---

# PROGETTO DA IMITARE
Nessun progetto spicca per qualità in qualche categoria.
ProApes e Qbteam, i due progetti presenti su mega, hanno comunque impianto grafico della presentazione, studio di fattibilità e glossario da prendere come riferimenti.
ProApes ha impianto grafico ottimo e studio di fattiblità e glossario buoni.
Qbteam ha tutte e tre le sezioni valutate come buone ma nello studio di fattiblità presenta qualche errore tipografico e grammaticale.

## LINEE GUIDA

## LETTERA DI PRESENTAZIONE

## NORME DI PROGETTO

## ANALISI DEI REQUISITI

## STUDIO DI FATTIBILITÀ

## PIANO DI PROGETTO

## PIANO DI QUALIFICA

## GLOSSARIO

## VERBALI

---

# ISTRUZIONI

* Creare un feature branch collegato alla issue
* Creare una copia di questo file intitolata anno-anno_report-progetti.md
* In "valutazione" scrivere gli errori da evitare / attenzioni da avere / indicazioni del prof suddivisi per documento; se le indicazioni sono generali inserirle in linee guida. 
* In "progetto" individuare un progetto eccellente e analizzare per quali motivi è stato reputato eccellente (descrivendone i contenuti e altre caratteristiche significative). Non soffermarsi solo al progetto nella RR ma vedere come il progetto è evoluto nel tempo, sopperendo a eventuali mancanze evidenziate dal prof
* Fare commit e chiudere il branch