## 25/11/2020

# ImolaInformatica

## Docker

### Container ed ecosistema docker
Solitamente per far girare una macchina virtuale si pone sul sistema operativo di base un hypervisor (per esempio xen o virtualbox) e su di esso la si fa girare. 
Le macchine virtuali al loro interno hanno il sistema operativo, delle librerie e le applicazioni.
Nel caso di docker, sul sistema operativo di base si installa il docker engine e su di esso si pongono librerie e applicazioni.
In questo modo si salta lo strato del secondo sistema operativo garantendo comunque l'isolamento.
L'insieme di librerie e applicazioni, impacchettato, viene chiamato container.
Nel caso dei server spesso non viene installato un sistema operativo di base ma delle macchine virtuali con al loro interno un docker engine e dei container.
Il vantaggio principale della containarizzazione è la standardizzazione. Il pacchetto può essere eseguito su qualsiasi sistema con docker installato, senza preoccuparsi delle dipendenze delle applicazioni, poichè esse sono già risolte nel pacchetto.
I container vengono eseguiti come processi isolati ma condividono lo stesso kernel il che porta a prestazioni migliori rispetto all'esecuzione di più macchine virtuali.
Docker permette sia di creare nuove applicazioni sia di scaricare applicazioni esistenti ed eseguirle.

### What is docker?
Docker consiste di due componenti principali:
- Docker Engine: installato sul proprio pc.
- Docker Hub: un servizio che permette di scaricare immagini ma anche di caricare le proprie, una sorta di repository.

### Docker inception
Visti i dati sull'utilizzo è da considerarsi uno standard de facto.

### Docker - Under the hood
Scritto in Go, linguaggio fatto da Google, molto performante e con sisntassi molto simile a C.
Docker è stato standardizzato da Open Container Initiative e Cloud Native Computing Foundation.
Oramai docker è compatibile con quasi tutti gli os.
Su Windows nelle versioni meno recenti non funziona bene perchè crea una virtual machine attraverso Hyper-V con all'interno Linux e vi pone un container collegato alla command-line di Windows.
Su Windows server e soprattuto su Linux, per il quale docker è stato pensato, è nativo, quindi non è necessario creare una virtual machine.
Per MacOS è presente un tool.
E' consigliato utilizzare docker su Linux perchè funziona meglio.

### L'architettura di Docker
Il sistema docker è costituito da due macrocomponenti, una in remoto e una in locale.
Docker Hub è in remoto mentre in locale vengono installate due cose:
- client
- daemon
Il client da comandi al daemon.
Comandi principali:
- docker build: per creare una nuova immagine
- docker pull: per scaricare immagine dal registry di docker hub
- docker run: per eseguire l'istanza di un container

### Docker objects
Le immagini docker sono dei template read-only. Possono contenere qualsiasi applicazione, anche sistemi operativi interi.
I container sono simili a directory. Contengono tutto il necessario.

### Docker components
La docker command line interface può rivolgersi al docker daemon presente nell'host locale oppure ad uno situato in remoto.
Si possono creare dei registry privati locali.

### Docker Container Lifecycle
Se si vuole containerizzare un'applicazione i passaggi sono:
1- Scrivere il Dockerfile nel quale vanno definiti tutti i passaggi per eseguire l'applicazione. Nel caso di app java quello che serve è la java virtual machine.
2- Eseguire la build, che crea l'immagine, la tagga e la pone nel repository locale.
A questo punto si può lanciare l'immagine, fare il push su un registry (per esempio quello di docker hub) oppure salvarla in un file di backup.

### Docker images
Un'immagine docker è un insieme di layer. Tutte le immagini contengono un layer di base senza contenuti.
Successivamente vengono installate tutte le librerie sempre sotto forma di layer.
Vantaggi dei layer:
- sistema performante perchè se più applicazioni hanno alcune dipendenze in comune i layer corrispondenti potranno essere riutilizzati.
- utilizzo efficiente del disco, per lo stesso motivo della voce precedente
- facilità di modifica

### Naming convention
[hostname[:port]]/[username]/reponame[:tag]
- hostname/port: indirizzo e porta del registro
- username: da usare nel caso il registry sia privato
- reponame/tag: nome dell'immagine e suo tag
Se si omettono hostname/port o username si va su DockerHub. Se si omette il tag, viene posto di default a "latest".

### Docker CLI
- docker pull: scarica l'immagine pronta per essere lanciata.
- docker build: crea un'immagine della directory fornita come parametro. Aggiungendo -t e una stringa si può porre un tag all'imagine che verrà creata.
- docker run: esegue un'immagine. Con un comando del tipo docker run -it ubuntu /bin/bash si può far partire l'esecuzione di un'immagine con la quale si potrà interagire tramite bash. Non è consigliato perchè rompe l'incapsulamento. Solitamente si interagisce tramite porte http.
- docker stop: ferma l'esecuzione dell'immagine
- docker start: fa ripartire l'esecuzione
- docker exec -it containerId /bin/bash: permette di lanciare comando ad un container già in esecuzione
- docker container <<command>>:
    - ls: fa vedere i container presenti. Col parametro -a fa vedere anche quelli stopped.
    - rm <<containerName>>: rimuove un container
-docker image <<command>>:
    - ls: fa vedere le immagini presenti sul sistema
    - rm: elimina l'immagine specificata

comandi utili del dockerfile:
- FROM ubuntu: installa ubuntu.
- RUN: lancia l'applicaizone.
- EXPOSE: espone la porta a cui ci si connetterà dall'esterno.

### Docker networking
Se non si definiscono delle porte esposte il container è completamente isolato.
Per fare questo si può usare il comando docker run --network none ... .
Con il comando docker run -d -p 127.0.0.1:80:80 ... invece si esegue un container esponendolo alla rete locale.
Precisamente il container potrà essere acceduto tramite l'indirizzo 127.0.0.1:80 (il primo 80 indicato nel comando) e i comandi saranno inoltrati alla porta 80 (il secondo 80) esposta dal container.
Se non si definisce un'interfaccia (quindi il comando contiene solo 80:80) il container sarà accessibile attraverso tutte le interfacce della macchina, pubbliche e private.

### Container data persistence
Di default i file dell'host non sono condivisi col container.
Tutto ciò a cui il container ha accesso è ciò che è stato definito durante la creazione.
Si può effettuare un bind mount, ovvero il mount di una porzione del filesystem dell'host nel filesystem del container. Per farlo bisogna definire dei volumi con comandi del tipo docker run -d -v <<cartella_dell_host>>:<<cartella_del_container>>
Attenzione ai permessi all'interno dei volumi: solitamente sono diversi da quelli presenti nel filesystem dell'host.

### Portainer web interface
Portainer è una web interface per la gestione di docker sulla macchina.

### Restart policy
Per un container, con il parametro --restart si può specificare la restart policy:
- no: il container non viene riavviato automaticamente (default).
- on-failure: se avviene un errore che chiude l'esecuzione del container questo viene riavviato automaticamente.
- unless-stopped: il restart del container è eseguito a meno che il container non sia esplicitamente in pausa oppure che Docker sia in pausa o riavviato. 
- always: il container viene eseguito ad ogni avvio della macchina.

### Contatti
email: lpatera@imolainformatica.it
twitter: @Lorenzopatera
linkedin: lorenzopatera


## Blockchain

### Il problema della fiducia
Attualmente il  sistema economico è basato su delle parti fidate.
Se devo scambiare denaro con qualcuno mi affido a un terzo (banca) per essere certo che chi deve versare il denaro lo abbia.
Svantaggi:
-i miei dati sono controllati dalla banca
-la banca costa
-in tre c' èpiù rischio di errori che in due
Soluzione: Distributed Ledger Technology ( Libri Contabili Distribuiti)
Ogni persona che vuole fare uno scambio può controllare sul DLT se la controparte ha i soldi.
E' distribuito, ovvero ha più copie posti diversi, quindi deve avere concordanza tra le varie copie.

### Caratteristiche dei DLT:
- Centralizzato: se uno dei nodi ha un ruolo particolare, ad esempio da il consenso sulle copie.
- Decentralizzato: se tutti i nodi sono paritari.
- Permissionless: chiunque è libero di farne parte.
- Permissioned: il permesso ad entrare deve essere accordato da un ente.
- Tokenized: vi si utilizza una valuta digitale come premio o come merce di scambio.
- Tokenless: non vi si utilizza una valuta digitale.
In una rete libera in mancanza di token tutti potrebbero entrare e porvi qualunque tipo di dato. I token permettono di regolare il comportamento all'interno del dlt.

### Blockchain
E' un esempio di DLT.
I dati sono raggruppati in blocchi e concatenati attraverso funzioni matematiche.
Sulla blockchain rimane tutto lo storico delle operazioni.
Il problema della fiducia è risolto dalla blockchain perchè ci sono più copie.
Le varie copie devono essere coerenti.
Ci vogliono meccanismi per il consenso sulla validità della copia

### Il problema del consenso
Se due copie sono diverse potrebbero contenere dati in conflitto.
Il problema nasce dai ritardi nella comunicazione tra le varie copie.

### Strumenti utilizzati
Funzioni hash: funzioni matematiche non invertibili.
Crittografia asimmetrica: ogni attore ha una chiave pubblica e una privata.
Se A cifra un messaggio con la chiave pubblica di B esso si potrà decifrare solo con la chiave privata di B. Si ottiene così confidenzialità.
Se A cifra un messaggio con la propria chiave privata esso si potrà decifrare solo con la chiave pubblica di A. Quindi se un messaggio è decifrabile con la chiave pubblica di A si può essere sicuri che è stato cifrato con la sua chiave privata. Si ottiene così autenticazione.

### Struttura di una blockchain
E' una catena di blocchi e ogni blocco contiene:
- da 1 a n transazioni, con n limitato a un massimo fissato a seconda dell'implementazione.
- l'hash del blocco precedente
- metadati variabili
L'hash permette di avere una struttura immutabile.

### Scambio di dati
L'utente effettua transazioni tramite il suo wallet.
Ci sono nodi della rete che validano le transazioni e le inseriscono nella blockchain.
Il wallet è una coppia di chiavi pubblica e privata che servono a firmare le transazioni.

### Algoritmo di consenso
E' necessario che sia stabilito tra i nodi un algoritmo per decidere cosa è valido.
Si basa su un meccanismo di validazione.
Due dei principali:
- Proof of Work: si basa sul fatto che un utente miner dovrà risolvere un problema posto dalla rete per poter creare il successivo blocco della catena.
Chi crea un blocco ottiene un premio, per esempio in criptovaluta e quindi gli  utenti gareggieranno.
- Proof of Stake: gli utenti dovranno congelare una parte dei token che possiedono per avere più probabilità di essere scelti per la creazione del prossimo blocco.
Bisogna scegliere il meccanismo giusto in base ai casi d'uso.
#### Confronto
PoW porta ad un aumento della richiesta di potenza computazionale, a differenza di PoS.
PoS ha una migliore scalabilità in termini di troughpu di transazioni.
PoS ha un rischio di centralizzazione, a differenza di PoW.
La blockchain è basata sul consenso della maggioranza, quindi è vulnerabile all'attacco del 50%+1, con entrambi i meccanismi: nel caso del PoW l'attacco è basato sul possesso di nodi, mentre nel caso del PoS è basato sul possesso di token.

### Punti di dibattito
Anche se è una tecnologia teorizzata da tempo sta prendendo piede solo da pochi anni.
#### Scalabilità
In alcuni casi viene applicata un'imposta sulla transazione. Se il traffico aumenta il costo aumenta.
#### Costo ambientale del mining
La rete di Bitcoin produce circa l'1% delle emissioni di CO2 a livello globale.
#### Privacy
Se qualcuno pubblica dei miei dati personali su una blockchain questi non potranno mai essere rimossi.
#### Hype
Vista la popolarità della blockchain spesso si cerca di utilizzarla anche in contesti a cui non è adatta.

### Possibili applicazioni

- #### Criptovalute
##### Bitcoin
Bitcoin è stata la prima criptovaluta.
Lo scopo è finanziario.
Utilizza il Proof of Work.
##### Ethereum
E' nata dopo Bitcoin ed ha imparato dai suoi difetti.
Ha maggiore potere espressivo grazie agli smart contract, ovvero delle applicazioni che possono essere messe sulla blockchain e possono essere attivate facendo una transazione. Si basano su un liguaggio Turing-completo che permette applicazioni più vaste rispetto a Bitcoin.
Un esempio di applicazione è Cryptokitties, un gioco basato sull'allevamento virtuale e sul commercio di gatti.
Finora ethereum ha usato un meccanismo di Proof of Work ma nel giro di qualche giorno dovrebbe passare al Proof of Stake.

- #### Filesystem distribuiti
Si può usare per distribuire file in modo tale che non possano essere modificati.
I file possono essere troppo grandi per essere inseriti su un unico blocco e quindi il tempo caricarli potrebbe diventare eccessivo.
Soluzione: InterPlanetary File System
E' un filesystem distribuito che permette di caricare file anche di grandi dimensioni e poi di ritrovarli tramite il loro hash.
Si potrebbe caricare l'hash del file su una blockchain modo da poter ritrovare il file e anche di garantire che il file non possa essere modificato. Per aggiungere confidenzialità basterebbe cifrare i file e condividere le password solo con chi deve acedervi.

- #### Self Sovereign Identity
Attualmente le nostre identità digitali sono in mano a degli enti (Google, Stato Italiano). Con la SSI invece tutti i nostri dati sono sotto il nostro controllo.
Funzionamento: L'utente presenta i propri dati personali a un validatore che li firma, poi l'utente li controfirma e l'hash dei dati viene caricato su una blockchain. Per dimostrare la validità dei dati basterà far confrontare il loro hash con quello presente nella blockchain.

- #### Notarizzazione su blockchain
In Italia e in tutti gli altri stati membri dell'UE i documenti notarizzati con tecnologie basate su sistemi distribuiti tramite timestamp hanno valore legale.

### Caso d'uso Imola Informatica
Tracciamento di una filiera industriale utilizzando la notarizzazione su blockchain.
Ci sono delle cartucce per la stampa riutilizzabili identificate da tag rfc che vengono distribuite a un attore. Una volta svuotate andranno ricaricate e rimesse in circolo. Per verificare che i passaggi siano stati eseguiti viene scannerizzato il tag nfc e i dati vengono inviati ad un server.
Questi dati vengono aggregati, hashati e caricati su blockchain.
Così la vita della cartuccia è memorizzata e si può visualizzare tramite un sito block explorer.