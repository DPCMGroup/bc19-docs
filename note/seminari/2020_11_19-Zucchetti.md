## 19/11/2020

# ZUCCHETTI

## Presentazione Zucchetti
Zucchetti è software house, ossia "costruisce software e vende bit" diversa dalle aziende system integrator, che fanno progetti e vendono forza-lavoro, ore-uomo. Quindi Zucchetti è interessata alla lungimiranza del prodotto sw, ad avere codice riutilizzabile in altri contesti e che duri nel tempo.

## Algoritmi di machine learning vs uomo
 Gli algoritmi di machine learning sono carenti rispetto all'occhio umano quando ci troviamo in un ambiente in cui l'uomo è abituato a percepire le cose ( 2 - 3 dimensioni). L'occhio umano è in difficoltà quando trattiamo con molte dimensioni.

## D3JS
Libreria che consente di spostarci da una visualizzazione a n dimensioni a 2-3 dimensioni

## Esempi live
Analizziamo i dati vedendoli dall'occhio umano e secondo l'interpretazione di diversi algoritmi.

* _configurazione a 3 blocchi di dati_
	algoritmo kMeans(3): funziona
	HC(3) - hierarchical cluster): funziona
	EM - Expectation–maximization: funziona
	dbscan: funziona

	Nota: perché gli algoritmi possano funzionare correttamente bisogna fornire il numero delle aree

* _configurazione a 2 blocchi di dati + gruppo centrale_
	kMeans(3) + HC(3): suddivisione errata
	EM e dbscan: vincono

* _configurazione smile_
	kMeans(3), HC(3), EM: falliscono
	dbscan: riconosce occhi, sorriso, sagoma del viso

* _configurazione topolino_
	dbscan: non efficace
	kMeans(3): riconosce le parti ma "squarta" Topolino
	HC(3): meglio del dbscan
	EM (expectation max.): funziona

* _configurazione a 2 blocchi + dati isolati_
	kMeans(3), HC(3): falliscono
	EM: funziona
	dbscan: funziona solo per i blocchi

* _configurazione: "salamotto" + dati isolati_
	kMeans: fallisce
	HC, EM: funziona
	OneClassGaussian / algoritmi che trattano punti isolati: funzionano

* _configurazione poco densa, 2 blocchi uniti da un filamento_
	dbscan: fallisce
	kMeans(3): individua le 3 aree
	HC: funziona

### Morale
* Un algoritmo non è sempre valido in tutte le situazioni
* L'occhio umano può selezionare l'algoritmo corretto quando è messo nelle condizioni di farlo (ossia in una visione comprensibile all'uomo)
* Bisogna quindi essere in grado di passare da n dimensioni a 2-3 dimensioni

## Metodi per manipolare più dimensioni
* Selezione delle dimensioni da visualizzare e scartando quelle meno significative
* Selezione caratteristiche di proiezione (in 2d, in 3d) per vedere meglio i dati
* Costruisco delle proiezioni basandomi sugli algoritmi (utilizzando la distanza fra gli oggetti o altre caratteristiche)

### SCATTERPLOT MATRIX A 4 DIMENSIONI
Esempio: dataset iris
* Si prendono le dimensioni a coppie (es. sull'asse y lunghezza sepali e larghezza dei sull'asse x)
* Osservazioni importanti si evincono sulle proiezioni che hanno sugli assi (lunghezza e larghezza dei petali) in cui i 2 blocchi di dati ottenuti sono rappresentativi di 2 tipo di iris diversi(si scartano quindi le proiezioni poco significative)

### PROIEZIONE DEGLI ASSI
* Esempio: 2 palle viste dall'alto. Non capisco che sono 2 palle finché non cambio gli assi, spostandomi verticalmente e sono in grado di distinguerle
* Esempio: blocchi 3 dati percebili manipolando gli assi di proiezione

### PROIEZIONI BASATE SU ALGORITMI
* _PCA_: indivua gli assi vedendo dove si esprime al massimo la varianza
* _t-SNE + UMAP_: non effettua solo la rotazione degli assi come PCA ma considera la distanza fra i punti ed è in grado così di separare i punti in gruppi. L'effetto è quello di scorporare i dati per vicinanza.
* _Matrice_ (es. interazioni fra personaggi dei Miserabili). Se i punti sono vicini fra loro sono avvenute interazioni. È possibile una riorganizzazione tematica dei punti (per cluster, nomi, etc...) e grazie a questo si scoprono relazioni all'interno del romanzo, personaggi che mettono in contatto gruppi fra loro, personaggi isolati.
- _Grafo di forza_: blocchi di dati vicini si avvicinano fra loro mentre se distanti si respingono (gli archi ci fanno capire queste forze in gioco)

Consiglio: analizzate la libreria D3JS

## Esempi 
* Rete Twitter: t-SNE
* Gruppi di persone associate da Amazon: kMeans 
* Regioni italiane e disoccupazione

## Domande
D: Ci interessa visualizzare solo dati che hanno già una label oppure sono senza label?
R: Fornire i dati di una label può essere estremamente costoso. Quello che conviene fare e il progetto si inserisce in questa ricerca è prevedere una fase esplorativa, nella quale non so ancora bene cosa ho di fronte e tramite l'occhio umano e visualizzazioni dei dati sono in grado di associare l'algoritmo corretto ed effettuare tag corretti. La sequenza nell'analisi del dato prevede: la raccolta del dato, la pulizia del dato, l'esplorazione umana alla ricerca degli algoritmi corretti, definizione del modello, applicazione degli algoritmi. Molti saltano l'esplorazione, che ci aiuta a capire quali siano gli algoritmi migliori.  La legge sulla privacy dei dati stabilisce che una persona sia in grado di dire perché è stato scelto un algoritmo
