##12/11/2020

Verbale integrativo rispetto alle slide usate durante il seminario.

Presentazione SyncLab:

Slide Problema...:
	L'obiettivo del progetto è dare un approccio pratico al machine learning.
    	Dobbiamo occuparci noi di indivuare e raccogliere i dati di input.
Slide Risorse disponibili:
	Abbiamo massima libertà nella scelta degli strumenti da usare, scegliamo in base alle nostre conoscenze e attitudini.
	Stessa cosa per le librerie.
    	Il linguaggio più utilizzato nell'ambito è python.
	La libreria più famosa è Tensorflow, di Google.
	PyTorch è l'antagonista, fatto da Facebook.
	Keras, scritto in python, permette di creare strutture in linguaggi di più basso livello, tipo Tesnorflow, ma in modo più snello e intuitivo.
	E' molto usato in ambito lavorativo perchè riduce costi di produzione e realizzazione. 
	Nel progetto useremo sicuramente Scikit-learn, che contiene una vasta gamma di algoritmi di machine learning ed è la libreria più utlizzata per il preprocessing dei dati.
	Per il preprocessing sono usate anche Pandas e Numpy.

Slide Risorse:
	Libro Hands-on ... di Aurelien Geron: Contiene tanto codice, esempi e progetti sviluppati dall'inizo alla fine.
	Libro Python ...: Più teorico. Spiega la matematica e la statistica che ci stanno dietro.
	
	Sul GitHub di Aurelien Geron ci sono i codici presenti nel suo libro.
	Kaggle è una community famosa per le competizioni nell'ambito machine learning.
	Vi sono presenti molti database utili per imparare ed esercitarsi.
	Molto utile perchè per ogni competizione ci sono codice e soluzioni forniti dagli utenti. 
	Google scholar è utile per leggere i vari paper riguardo al machine learning.

Slide architettura:
	L'immagine rappresenta l'architettura proposta.
    	Nella prima parte bisogna raccogliere i dati e selezionare quelli più significativi.
	I dati devono confluire in un database attraverso un framework di streaming tipo Kafka (fa parte della famiglia Apache Spark).
    	I dati nel database devono essere storicizzati e organizzati.
	Ci sono due strade per fornire informazioni agli utenti: fornire i dati direttamente dal database oppure fornire predizioni basate su quei dati.
	Questa seconda strada si ottiene con il machine learning.
	Attraverso il machine learning si ottengono dei modelli a partire dai dati del database.
	Questi modelli serviranno per fare predizioni.
    	Poi bisogna produrre un'interfaccia/dashboard che l'utilizzatore finale può utilizzare per ricavare informazioni.
    	La dashboard può essere grafica o di altro tipo.

Slide architettura complessa:
        Lo schema rappresenta il reale svolgimento di un progetto di machine learning.
	Scoping:
		Noi studenti, nella parte di machine learning del progetto, ci occupiamo della sezione data science. 
		Deve interagire con le altre due sezioni: product e data engineering.
		Il produttore deve definire delle necessità nel proprio ambito lavorativo.
		Il data scientist individua una soluzione che risponda alle necessità e si rivolge al data engineer per capire come svilupparla.
		Se il data engineer valida lo sviluppo allora il data scientist propone la soluzione al produttore per capire se risponde ai bisogni individuati.
	Research:
		E' la fase fondamentale anche se spesso viene trascurata.
		Consiste nel cercare soluzioni esistenti e selezionare quelle che si possono adattare al tipo di dati che dobbiamo trattare.
		Questa fase può richiedere anche diverso tempo.
		La scelta che si effettua in questa fase influenza tutte le fasi successive.
		Questa fase serve anche a validare la soluzione scelta.
		Possiamo infatti giustificare la scelta basandoci su pubblicazioni e applicazioni esistenti.
		Una volta compiuta la scelta e compresi i suoi rischi e vantaggi bisogna presentarla nuovamente al produttore.
		Il produttore dovrà dare o meno il consenso.
		Da qui in poi il processo è lineare.
	Development:
	
	Deployment:
		Rilascio e validazione.
		Test con dati diversi per capire se i modelli prodotti hanno generalizzato il problema e sono riutilizabili.

Slide Data science:
	Il data scientist svolge queste 6 fasi:
        Research
        Data exploration
        Modeling
        Result Analysis
        A/B testing
        Productization

Slide Fasi di progetto:
	Noi dobbiamo percorrere questi 5 step:
	
	Data exploration:
        E una fase fondamentale.
	Capire quali dati sono importanti o necessari.
		
	Preprocessing:
	I dati devono essere presentati in maniera corretta agli algoritmi.
	
    Training

    Evaluation/Validation

    Deploy

Slide Data exploration:
	I dati vanno presentati all'algoritmo sotto forma di matrice.
	Nella matrice ci sono tutte le osservazioni(features) e il target a cui si vuole arrivare.
	Ogni riga si riferisce ad un unico target.
	Si possono mettere anche dati completamente diversi fra loro, per esempio temperatura e distanza.
	Non possono esserci dati mancanti e nemmeno outliers e i dati devono essere bilanciati, cioè tutte le possibilità/configurazioni devono essere presenti.
	Dati troppo correlati possono ridurre le performance del sistema.

Slide Preprocessing:
	Consiglio utilizzo Scikit-learn.
	Cleaning:
		Non ci devono essere dati mancanti.
	Normalizzazione:
		I dati devono essere scalati in modo che abbiano tutti lo stesso peso.
	Feature extraction:
		Si possono estrarre altre variabili/feature dal sistema, per aumentarne le performance.
	Train/Test set splitting:
		I dati vanno divisi tra dati per il training e dati per il testing. A volte si dividono in train/test/validation ma dipende dalla quantità di dati a disposizione.
		Spesso si sbaglia questa divisione.
        Modo giusto per farlo:
		  Se i dati sono temporali quelli recenti vanno in test. Così da poter capire se il modello riesce a prevenire l'immediato futuro.
		  Se invece i dati non sono temporali si fa uno split randomico.
		  Una volta fatto lo split è consigliato verificare che siano presenti tutti gli scenari possibili in modo bilanciato.

Slide Predizione:
	A questo punto dovremmo già aver capito qual è l'algoritmo da scegliere.
	Il problema può essere di tipo classificazione o regressione e per ogni categoria ci sono degli algoritmi adatti. 

Slide Scegliere l'algoritmo giusto:
	Non esiste una regola generale per scegliere l'algoritmo giusto, ci vuole esperienza.
	La scelta dipende dai dati con cui dobbiamo lavorare.
	Si consiglia di provare più algoritmi della stessa famiglia.
	
Slide Evaluation and validation:
	Una volta individuata la soluzione si può passare allo sviluppo, cioè scrittura del codice, allenamento e valutazione.
	La performance del modello si misura con metriche di tipo statistico.
	La scelta della metrica giusta dipende dal problema.
	Si consiglia di provare più algoritmi della stessa categoria e una volta scelto il migliore cercare di ottimizzarlo.
	Iperparametri: parametri che possono essere modificati dall'operatore esterno e che permettono di aumentare la precisione dell'algoritmo.
	Sono differenti a seconda dell'algoritmo.
	Sulle guide delle librerie si trovano gli iperparametri corrispondenti ai diversi algoritmi.
	Grid-Search, Random-Search: tecniche nelle quali si creano liste di valori degli iperparametri, si compongono tutte le loro possibili combinazioni e con queste si allenano vari modelli.
	I vari modelli si testano e tra di essi si trovano i migliori.
	Queste tecniche hanno un alto costo computazionale.
	Quindi può essere più conveniente fare trial and error con un parametro alla volta: si modifica un iperparametro fino a che non se ne trova un valore che migliora le prestazioni, poi si passa all'iperparametro successivo.

Slide Overfitting:
	Siccome i dati che useremo saranno ricavati online o generati da noi Synclab non si aspetta performance elevatissime.

	Overfitting: il modello ha imparato troppo dai dati che gli abbiamo fornito e ha basse prestazioni con dati nuovi. Il modello non ha generalizzato il problema.
	Underfitting: il modello non è abbastanza accurato. Il modello non ha compreso il problema. Non è abbastanza allenato oppure è troppo semplice.
	Per prevenire l'overfitting si fa lo split in vari set e se il modello ha performance simili in tutti allora va bene.
	
Slide Checklist:
	E' utile fare una checklist per vedere se abbiamo completato tutte le fasi.
	Una volta completata la checklist salviamo il modello per utlizzarlo con la dashboard.

Slide Outcomes:
	Alla fine del lavoro dobbiamo ottenere modelli e report.

	La fase di allenamento e utilizzo sono svincolate. L'utilizzo è facile e rapido, a differenza del training.

	Sarebbe bello scegliere più algoritmi, da confrontare tra loro, e poi riportar nel report l'esito del confronto.

Contatti:

Ing. Fabio Pallaro
	f.pallaro@synclab.it
Cristoforo Decaro
	cristoforo.decaro@synclab.it

Domande:
	Per splittare in maniera casuale come facciamo? generatore randomico di numeri? rumore?
		
		Cristoforo di solito fa split casuale e poi verifica con una rappresentazione grafica/istogramma se sono presenti tutte le possibli combinazioni di target.
		Cioè devono essere presenti in egual misura i vari target.
		Consiglio: usare uno stesso seed per il random ogni volta che si allena.
		Così ti trovi nella stessa situazione ogni volta, stessi dati negli stessi set.
		Se testi le performance di diversi modelli con diversi set non puoi fare un confronto valido.

	Bisogna ristudiare statistica?
		No. Bisogna semplicemente capire quale metrica è più adatta per l'approccio scelto e che significato ha il risultato fornito dalla metrica.
		Capire come le statiche sono legate alla bontà dell'algoritmo. Per esempio valore MSE basso => performance buona.
		

Vardanega:
	Non serve diventare esperti di machine learning per il progetto. Bisogna però approcciarsi ad esso come informatici.
	