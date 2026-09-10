# Novità

*[English](CHANGELOG.md) · Italiano*

Che cosa cambia per chi usa il programma, dalla più recente. Ogni versione viene pubblicata come
[pacchetto di installazione](../../releases) per Windows x64, in due lingue del setup.

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
