# Novità

*[English](CHANGELOG.md) · Italiano*

Che cosa cambia per chi usa il programma, dalla più recente. Ogni versione viene pubblicata come
[pacchetto di installazione](../../releases) per Windows x64, in due lingue del setup.

---

## 1.50.0 — linguetta Note, esportazione per schede e cronologia locale con tutti i passaggi

**Nuove funzioni**
- **Linguetta Note**, accanto a Destinazioni e Collegamenti: appunti liberi sulla scheda, da
  inserire, modificare, eliminare e riordinare. Una nota si può segnare **Importante**: compare in
  rosso e, se la scheda ne ha almeno una, in un banner sopra la griglia delle destinazioni — due righe
  al massimo, con i puntini quando non ci sta tutta; un clic sul banner apre la linguetta Note.
- **Esportazione e importazione per schede**: la finestra di esportazione fa scegliere quali schede
  entrano nel file — un solo server o tenant da condividere con un collega, oppure l'elenco intero
  come backup personale — e se includere i **collegamenti** (spuntato di default) e le **note** (non
  spuntato, perché una nota può contenere appunti personali o riservati). Il menu del tasto destro
  sulla linguetta ha la nuova scorciatoia «Esporta scheda…». L'importazione aggiunge a una scheda già
  presente solo i collegamenti e le note che le mancano. Preferiti e righe nascoste non viaggiano più
  nel file.
- **Cronologia locale con tutti i passaggi**: un'operazione non si riduce più all'ultimo messaggio.
  Ogni passaggio — invio del pacchetto, distribuzione in coda e in esecuzione, sincronizzazione,
  aggiornamento dei dati, installazione, rimozione delle versioni precedenti — resta con ora di
  inizio, ora di fine e durata, anche sulle destinazioni OnPrem. Si registrano anche le attese
  (un'altra estensione in pubblicazione, il turno dentro una cartella), con quante volte si è
  ricontrollato, e l'account con cui si è lavorato; il testo si chiude con la durata totale. Ogni voce
  viene scritta appena la sua riga si conclude: una pubblicazione da cartella lascia una voce per app.
  Nei dettagli di una riga della coda gli stessi passaggi si leggono mentre l'operazione è ancora in
  corso.

**Coda delle attività**
- Una sola colonna **Destinazione** («istanza [scheda]») al posto di server/tenant e
  istanza/ambiente; la colonna che ripeteva la stessa coppia è sparita, e «Errore / Output» diventa
  semplicemente «Output». Una riga già riprovata non si può più riprovare: «Riprova non riuscite»
  rimette in lavorazione solo l'ultimo tentativo di ogni lavoro.
- **Quando una pubblicazione aspetta** perché sull'ambiente ne è già in corso un'altra, il motivo dice
  anche **chi** la sta eseguendo — o «non registrato» se l'ambiente non lo dichiara, per esempio per
  una pubblicazione da VS Code.
- Un errore momentaneo di rete o del servizio durante l'attesa di una pubblicazione o disinstallazione
  SaaS non segna più come fallita un'installazione ancora in corso: DYNAMO riprova la lettura dello
  stato invece di arrendersi.

**Altre modifiche**
- Il pulsante del **catalogo AppSource** compare solo sulle schede online, dove il catalogo funziona.
- Un errore gestito (per esempio un salvataggio automatico non riuscito) resta visibile in rosso
  nella barra di stato finché non si risolve o non lo si chiude con la nuova «×». Le impostazioni di
  connessione aperte dal menu del tasto destro sulla linguetta modificano sempre la scheda su cui si è
  cliccato. Impostare la finestra di aggiornamento o pianificare un aggiornamento conferma anche
  l'esito positivo in una finestra.
- Nelle finestre di sessioni, configurazione, operazioni pianificate, operazioni app, licenza e
  servizi web un errore lungo si accorcia a poche righe e si apre per intero con un clic.
- All'avvio la notifica di un aggiornamento disponibile aspetta che la scheda iniziale abbia finito di
  rileggersi; «Aggiorna ora» mostra sempre la finestra con le note di rilascio, anche a operazioni
  ancora in corso — il blocco vale solo per lo scaricamento.
- Aggiungere o aggiornare un server o un tenant che fallisce mostra di nuovo la finestra d'esito
  invece di sparire in silenzio; un tenant con lo stesso nome di una scheda OnPrem già esistente
  avvisa con una finestra propria.
- Nell'intestazione della scheda il conteggio «(+N nascoste)» resta cliccabile anche dopo aver acceso
  «Mostra tutto»; una scheda senza collegamenti non dice più «0 collegamenti».

---

## 1.49.0 — catalogo AppSource, servizi web e API, cronologia locale

**Nuove funzioni**
- **Catalogo AppSource**: tutte le app per Business Central pubblicate per il mercato dell'ambiente,
  già elencate e filtrabili per nome ed editore, con la scheda completa di ciascuna. Da lì si
  installano, o si aggiornano se sono già presenti.
- **Servizi web e API** (nuovo menu Sviluppo): cosa una destinazione espone su OData V4, API e
  SOAP — comprese le API delle app installate — con indirizzi pronti, campi, metodi ed esempi di
  richiesta, risposta ed errore da incollare in un documento tecnico.
- **Simboli AL**: da Gestione estensioni si scaricano i simboli delle app installate su una
  destinazione, dai feed pubblici oppure direttamente dalla destinazione, che fornisce anche quelli
  delle per-tenant extension. Dal menu Sviluppo, «Scarica simboli Microsoft» prende dai feed
  pubblici i simboli delle app Microsoft per una localizzazione e una versione, senza bisogno di una
  destinazione.
- **Cronologia locale**: le operazioni che modificano una destinazione, lanciate da questo
  computer, restano in un registro locale con le opzioni scelte, i passi eseguiti e l'eventuale
  messaggio di errore.
- **Collegamenti nella scheda**: accanto alle destinazioni, una linguetta con i siti, le cartelle e
  le condivisioni di rete che le riguardano — il portale del cliente, la documentazione, la
  cartella dei pacchetti.

**Coda delle attività**
- **Le operazioni sulle estensioni aspettano che la destinazione sia pronta**: prima di ogni
  operazione su un'estensione, DYNAMO verifica che l'ambiente online non sia in aggiornamento e che
  non ci sia già un'altra distribuzione in corso — di un collega, da VS Code o da dentro Business
  Central —, e su un server che il servizio dell'istanza sia in esecuzione. Se la destinazione è
  occupata l'operazione resta in coda e parte da sola appena si libera; «Avvia adesso» scavalca
  l'attesa.
- **Riprova dalla coda**: una riga non riuscita si rilancia con le stesse opzioni del primo
  tentativo, senza ripartire dal menu; «Riprova non riuscite» le rilancia tutte insieme.

**Destinazioni**
- **Scheda informativa**: mostra le sessioni aperte e, sugli ambienti online, le distribuzioni in
  corso — le due cose da sapere prima di fermare un servizio o lanciare una pubblicazione. Accanto
  alla versione di Business Central, «Novità della …» apre le note di rilascio Microsoft di
  quell'aggiornamento, e lo stesso accanto alla versione di destinazione del prossimo.

**Altre modifiche**
- **Aggiungi scheda** sostituisce «Aggiungi server» e «Aggiungi tenant», e offre un terzo tipo: una
  scheda senza destinazioni, fatta di soli collegamenti. Una scheda locale resta in elenco anche
  quando la rilevazione non trova servizi.
- I collegamenti si possono raccogliere in **gruppi**, che viaggiano con l'elenco esportato.
- Un nuovo esito **Programmata** nella coda, per ciò che l'ambiente ha accettato ma non ha ancora
  eseguito, distinto da *Saltata*, che non si farà.
- In Gestione estensioni un'app con un aggiornamento disponibile dice **Da aggiornare** nella
  colonna Stato.
- La colonna su cui si ordina una griglia mostra una freccia, e la coda delle attività resta sempre
  in ordine di arrivo.
- All'avvio, con Business Central installato sul computer, la scheda localhost è già pronta e si
  allinea da sola alle istanze installate; aprendo il web client, la company usata l'ultima volta
  sta in cima all'elenco.

---

## 1.48.5 — operazioni pianificate e aggiornamento dei dati

Online un'estensione si può ora pubblicare nella finestra di aggiornamento dell'ambiente, e la nuova
finestra **Operazioni pianificate** elenca ciò che partirà più tardi da solo — estensioni in attesa
della finestra o del prossimo aggiornamento, aggiornamenti di app, il prossimo aggiornamento
dell'ambiente — e annulla ciò che Business Central consente. In Gestione estensioni un'estensione
per tenant con una versione nuova già pianificata lo dice, e la pianificazione si toglie da lì. In
locale la pubblicazione non fallisce più quando Business Central richiede l'aggiornamento dei dati —
per esempio dopo che la versione precedente è stata disinstallata con i dati ancora presenti:
l'aggiornamento viene eseguito, oppure si rimanda con il nuovo comando **Aggiorna dati** e la colonna
**Aggiornamento dati** di Gestione estensioni. La barra degli strumenti ora si adatta alla larghezza
della finestra, e le schede mostrano il tipo di destinazione con un'icona.

---

## 1.48.4 — più sicurezza sui sistemi di produzione

Una revisione di tutte le operazioni che scrivono su Business Central ha stretto i punti in cui un
comando faceva più di quanto la conferma dicesse. In locale un'estensione da cui dipendono altre
estensioni installate non viene più disinstallata — vengono elencate e vanno tolte prima, come
online — e ripubblicare la stessa versione in ForceSync ora rimette al loro posto quelle
estensioni, con i loro dati. Le conferme nominano il server o il tenant vero di ogni destinazione,
la seconda conferma di ForceSync parte da "No", un ambiente online viene ricontrollato subito prima
di essere eliminato, e un elenco importato viene verificato prima di essere usato. Gli elenchi di
estensioni si leggono meglio, e la coda delle attività mantiene i colori anche in inglese.

---

## 1.48.3 — segnalazioni e aggiornamenti più semplici

Ora si può segnalare un problema o proporre qualcosa direttamente dal menu "?" o dalla finestra
Informazioni: entrambi aprono un modulo già pronto su questa pagina. Il controllo degli
aggiornamenti è ora un semplice interruttore acceso/spento, verificato in automatico a ogni
apertura del programma, invece di un numero di giorni. Il programma di installazione può aprire
DYNAMO in automatico appena finito il setup, con una casella nell'ultima schermata. Chiude il
rilascio qualche rifinitura minore dell'interfaccia.

---

## 1.48.2 — rifiniture dell'interfaccia

Questa versione riorganizza alcuni comandi e ottimizza il layout in diverse aree dell'interfaccia.

---

## 1.48.1 — la barra segue la destinazione

La barra degli strumenti mostra solo i pulsanti che hanno senso per la scheda selezionata: i
comandi sul servizio e la licenza restano solo OnPrem, un nuovo pulsante Admin Center apre il
portale del tenant SaaS, e un nuovo pulsante Eventi apre il registro eventi di un ambiente. Su un
ambiente nel cestino resta disponibile solo il ripristino, finché non torna indietro.

---

## 1.48.0 — primo rilascio

La prima versione pubblicata qui, con l'insieme completo delle funzionalità del programma. Le
versioni precedenti non sono state distribuite.

---

Le note delle versioni precedenti alla 1.48.0 sono disponibili su richiesta.
