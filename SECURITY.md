# Security policy

*English · [Italiano](#politica-di-sicurezza)*

DYNAMO administers Business Central services on production systems, and it does so with the rights
of whoever runs it. A defect here does not break a build — it stops an ERP. Reports are welcome and
are taken seriously.

## Supported version

Only the **latest published version** receives fixes. Before reporting, check that the problem is
still there on the version in [Releases](../../releases/latest).

## How to report

Open an [issue](../../issues) and write `[security]` at the start of the title.

If the problem can be abused as it stands, **describe the class of the problem and the effect, not
a working recipe**. That is enough to reproduce it and it does not hand a ready exploit to whoever
reads the issue in the meantime. If you would rather not write it in the open at all, open an issue
saying only that you have a security report and asking for a private channel.

Expect a first reply within a few days. There is no bounty programme.

## What never goes in a report

An issue is public and stays public. Never paste:

- names or addresses of servers, service instances, tenants or databases;
- tenant, environment or company identifiers;
- user names, passwords, tokens, connection strings or the content of a license file;
- error messages copied as they are — those coming from Business Central, PowerShell or Windows
  routinely carry server names inside them.

The version number, what you did, what you expected and what happened are enough to start. Where a
message matters, replace the identifying parts with placeholders.

## What is not a vulnerability

- **The package is not signed**, so Windows shows "Unknown publisher" on the elevation prompt. It is
  known and stated in the guide.
- **Administrator rights being needed** for Business Central instances on the same computer: those
  commands run inside the program, and the rights are the ones Windows requires.
- **Saved server passwords being readable by a local administrator of the machine.** Credentials are
  kept in the Windows Credential Manager, which protects them from the other users of the machine
  but not from an administrator of it. That is why the "Remember the password" box starts unticked.

---

# Politica di sicurezza

*[English](#security-policy) · Italiano*

DYNAMO amministra servizi Business Central su sistemi di produzione, e lo fa con i diritti di chi lo
esegue. Un difetto qui non rompe una build: ferma un ERP. Le segnalazioni sono benvenute e vengono
prese sul serio.

## Versione supportata

Riceve correzioni **solo l'ultima versione pubblicata**. Prima di segnalare, verifica che il
problema sia ancora presente nella versione che trovi in [Releases](../../releases/latest).

## Come segnalare

Apri una [segnalazione](../../issues) scrivendo `[security]` all'inizio del titolo.

Se il problema è sfruttabile così com'è, **descrivi il tipo di problema e l'effetto, non una ricetta
funzionante**. Basta per riprodurlo e non consegna un exploit pronto a chi legge la segnalazione nel
frattempo. Se preferisci non scriverne affatto in chiaro, apri una segnalazione dicendo solo che hai
un rilievo di sicurezza e chiedendo un canale riservato.

Una prima risposta arriva entro qualche giorno. Non esiste un programma di ricompense.

## Che cosa non va mai in una segnalazione

Una segnalazione è pubblica e resta pubblica. Non incollare mai:

- nomi o indirizzi di server, istanze di servizio, tenant o database;
- identificativi di tenant, di ambienti o di company;
- nomi utente, password, token, stringhe di connessione o il contenuto di un file di licenza;
- messaggi d'errore copiati così come sono: quelli che arrivano da Business Central, da PowerShell o
  da Windows contengono abitualmente nomi di server.

Il numero di versione, che cosa hai fatto, che cosa ti aspettavi e che cosa è successo bastano per
cominciare. Dove il messaggio conta, sostituisci le parti che identificano i sistemi con dei
segnaposto.

## Che cosa non è una vulnerabilità

- **Il pacchetto non è firmato**, quindi Windows mostra «Autore sconosciuto» alla richiesta di
  elevazione. È noto e dichiarato nella guida.
- **I diritti di amministratore richiesti** per le istanze Business Central sullo stesso computer:
  quei comandi vengono eseguiti dentro il programma, e i diritti sono quelli che Windows pretende.
- **Le password dei server salvate, leggibili da un amministratore locale della macchina.** Le
  credenziali stanno in Gestione credenziali di Windows, che le protegge dagli altri utenti della
  macchina ma non da un suo amministratore. È il motivo per cui la casella «Ricorda la password»
  parte spenta.
