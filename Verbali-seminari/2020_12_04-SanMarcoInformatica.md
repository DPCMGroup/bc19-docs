## 04/12/2020

# San Marco Informatica
### Utilizzo di Docker come scelta architetturale

Per fare il confronto partiamo da una domada:
Le architetture che si possono oggi creare sfruttando il concetto di container si possono realizzare anche in altro modo?
Si,però spendendo ovviamente più tempo (manutenzione, creazione), risorse, fatica e soldi
I container sono quindi la soluzione a tutti i problemi?
No. Non avranno mai le performance elevate di un'installazione su macchina fisica. Inolte tale struttura non è sempre predisposta per ospitare basi di dati.
Non disegnata per applicazioni con UI e non "portabile".

### L'importanza di un'architettura ben studiata
Bisogna pensare prima a cosa abbiamo bisogno poi
Bisogna pensare a priori tutti i requisiti anche di crescita del nostro prodotto per fare in modo che in futuro non siamo vincolati.

### Balancer
Utile utilizzare il container se ho un infrastruttura distribuita orizzontalmente (stessa cosa riprodotta in più macchine) e quindi molte macchine da collegare. Altrimenti ciò complica solo il lavoro.
Il balancer nasce come bilanciatore di carico e gestore di fallback. Le operatività più comuni sono:
-Preferred: Quell'utente preferibilmente utilizza quell'istanza del server
-Alternate: Ogni singola chiamata è portata sulla macchina 1 o 2 esattamente al 50%
-Fallback: cosa più importante, garantisce che se la macchina 1 cade tutto il carico va sulla macchina 2

### Esempio 1: Server Merging
Requisiti:
-Un gioco prevede utenti che combattono tra loro.
-Ogni utente sara ospitato su un server e potrà scontrarsi solo con altri utenti dello stesso server
-Se l'utente dovesse decidere di cambiare server, tutti i suoi progressi saranno persi.
-Per mantenere alto l'engagement dell'utente, i server devono essere sempre ben "popolosi" di utenti attivi.
-Posso accettare tempi di downtime.

Situazione iniziale:
Abbiamo un balancer e 4 server di cui due che hanno visto uscire utenti e quindi poco carichi (meno del 50%). C'è un database che dice al balancer per ogni utente dove dovrebbe essere indirizzato.
Non vogliamo i due server poco pieni e facciamo un merge tra i due. Quindi i dati di uno vengono migrati nell'altro andandolo quasi a riempire. Cosa migliore sarebbe prendere gli utenti dei due e metterli insieme in un quinto server nuovo.
Una volta completato il merge vengono eliminati i server vuoti previo beckup.

Vantaggi:
-Velocità di creazione di nuovi nodi.
-Velocità di accensione/Spegnimento di nodi già esistenti.
Ciò porta ad una riduzione dei tempi di downtime e nessuno spreco di risorse.

### Esempio 2: Canary Release (utilizzato per linkedin)
-Un'applicazione deve essere scalabile orizzontalmente.
-Devo poter rilasciare nuove funzionalità, non necessariamente sull'intero sistema (Linkedin ha aggiornamenti ogni due settimane)
-Ogni nodo del sistema deve poter avere una versuone diversa del software,
-Finchè il sistema non è interamente portato alla versione stabile alcuni utenti devono essere indirizzati solo su determinati nodi.
-Non devo avere tempi di downtime

Situazione inizale:
Balancer e qualche server replicati più registro che mappa utenti e server.
Degli utenti registrati come Alpha Tester possono accedere ad un determinato server aggiornato. Se la "prova" va bene viene aggiornato un altro nodo dove agiscono i BetaTester e così via, 
fino a completo aggiornamento del sistema.

Vantaggi:
-Velocità di aggiornamento del singolo nodo.
-Velocità di rollback in caso di errore
-Velocità e automatismi di adeguamento dell'intero sistema
ciò permette di avere pochi utenti con malfunzionamenti e nessuna procedura complessa.

### Chi controlla il controllore?.
Ci sono molte strategie per questo.
La soluzione più comune è dividere il balancer in base alle sue funzioni, ossia distinguere tra la componente fallback e la componente di bilanciamento applicativo.
Il fallback-balancer potrebbe essere a sua volta ridondato. In casi ad elevata criticità del sistema la soluzione può essere HW  e non SW.

### Esempio 3: Progetto Portacs

L'utilizzo dei sistemi sopra descritti all'interno del nostro progetto.

Necessità:
-L'applicazione deve essere sempre disponibile (no downtime)
-L'applicazione deve essere aggiornabile
-Deve esserci la possibilità di testare un nuovo algoritmo in maniera sicura
-L'applicazione non dispone di database.

Ipotesi iniziale (non è richiesto nel progetto, è un esempio):
C'è un componente che simula l'utilizzatore (robot, muletto, auto..) che deve mandare e ricevere dati dal componente di analisi real-time.
Deve esserci un monitor che fa vedere dove sono tutti i componenti (robot, muletto, auto..) del sistema in tempo reale.
Per la parte di elaborazione dei dati, i dati vengono inviati al balancer che ha due motori di calcolo divisi (master e redundancy) in modo tale che se uno cade ho comunque l'altro con i dati del motore di calcolo master.
Quando aggiorno il sistema chiudo l'interrutore del balancer e switchare tutte le chiamate al server ridondante in modo da aggiornare il master.



























