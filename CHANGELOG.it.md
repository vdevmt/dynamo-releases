# Novità

*[English](CHANGELOG.md) · Italiano*

Che cosa cambia per chi usa il programma, dalla più recente. Ogni versione viene pubblicata come
[pacchetto di installazione](../../releases) per Windows x64, in due lingue del setup.

---

## 1.45.0 — primo rilascio pubblico

La prima versione pubblicata qui. Le versioni precedenti non sono state distribuite.

Che cosa fa, a questa versione:

- **Destinazioni dei due tipi in un unico elenco.** Ogni scheda è un server locale o un tenant
  online; le righe sono le istanze di servizio o gli ambienti. Le schede si rinominano, si colorano
  e si riordinano, le righe si nascondono e si rimostrano, e una scheda Preferiti raccoglie righe
  prese da schede diverse.
- **Verifica di sola lettura** su ogni destinazione, che dice se il servizio risponde e se l'account
  è autorizzato a lavorarci, prima di cambiare qualsiasi cosa.
- **Avvio, arresto e riavvio** dei servizi locali, su tutte le destinazioni che evidenzi.
- **Gestione delle estensioni**: installazione, disinstallazione, annullamento della pubblicazione e
  sincronizzazione, con lo stato di ogni estensione, il publisher, la versione e — in locale — se è
  stata sincronizzata. La disinstallazione non cancella mai i dati.
- **Pubblicazione** di un singolo pacchetto o di un'intera cartella, nell'ordine ricavato dalle
  dipendenze dichiarate dentro ciascuno, con l'ordine mostrato e modificabile prima di confermare e
  una riga di coda per ogni app.
- **Confronto delle estensioni** di due destinazioni, anche di tipo diverso, e della
  **configurazione di due istanze locali**, mostrando solo le chiavi che differiscono.
- **Ambienti online**: creazione, copia, rinomina, cancellazione, ripristino a un istante nel tempo
  o dal cestino, finestra di aggiornamento, pianificazione dell'aggiornamento, registro eventi, e
  aggiornamento delle app del marketplace con l'intera catena delle dipendenze messa in coda
  nell'ordine giusto.
- **Il web client si apre sulla company che scegli**, così non compare la selezione company di
  Business Central; su un server la domanda arriva solo dove non è dichiarata una company
  predefinita.
- **Configurazioni per VS Code**: quella per sviluppare su una destinazione e quella di tipo attach
  per una sessione aperta in quel momento, presa da Sessioni attive.
- **Company, sessioni attive e licenza Business Central** di una destinazione, con la possibilità di
  chiudere una sessione e di caricare un file di licenza.
- **Una coda delle attività** che lavora con una corsia per destinazione — in sequenza dentro una
  corsia, in parallelo fra corsie diverse — con esito, durata ed errore completo di ogni operazione
  conservati finché non si svuota.
- **Inglese e italiano**, numeri, date e durate compresi, scelti dalle Impostazioni e indipendenti
  dalla lingua di Windows.

---

Le note delle versioni precedenti alla 1.45.0 sono disponibili su richiesta.
